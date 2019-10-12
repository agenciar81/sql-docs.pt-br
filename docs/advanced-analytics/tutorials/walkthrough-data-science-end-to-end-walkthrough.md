---
title: Tutorial para cientistas de dados usando a linguagem R
description: Tutorial mostrando como criar uma solução de R de ponta a ponta para análise no banco de dados.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/11/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: ad7f5a500f740e4a302f814ec9523dfb33ecc68b
ms.sourcegitcommit: 710d60e7974e2c4c52aebe36fceb6e2bbd52727c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72278270"
---
# <a name="tutorial-sql-development-for-r-data-scientists"></a>Tutorial: Desenvolvimento de SQL para cientistas de dados de R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Neste tutorial para cientistas de dados, saiba como criar uma solução de ponta a ponta para modelagem preditiva com base no suporte a recursos do R no SQL Server 2016 ou SQL Server 2017. Este tutorial usa um banco de dados [NYCTaxi_sample](demo-data-nyctaxi-in-sql.md) no SQL Server. 

Você usa uma combinação de código R, dados [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e funções SQL personalizadas para criar um modelo de classificação que indica a probabilidade de que o driver possa obter uma gorjeta em uma viagem de táxi específica. Você também implanta seu modelo R no [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e usa dados do servidor para gerar pontuações com base no modelo.

Este exemplo pode ser estendido para todos os tipos de problemas reais, como a previsão de respostas do cliente para campanhas de vendas ou a previsão de gastos ou de participação em eventos. Como o modelo pode ser invocado a partir de um procedimento armazenado, você pode incorporá-lo facilmente em um aplicativo.

Como o passo a passos foi projetado para introduzir desenvolvedores de R a [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], R é usado sempre que possível. No entanto, isso não significa que o R é necessariamente a melhor ferramenta para cada tarefa. Em muitos casos, o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] poderá fornecer um desempenho melhor, especialmente para tarefas como agregação de dados e engenharia de recursos.  Essas tarefas podem se beneficiar particularmente dos novos recursos do [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], como índices columnstore com otimização de memória. Tentamos destacar possíveis otimizações ao longo do caminho.

## <a name="prerequisites"></a>Pré-requisitos

+ [SQL Server serviços de Machine Learning com integração de r](../install/sql-machine-learning-services-windows-install.md#verify-installation) ou [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md)

+ [Permissões de banco de dados](../security/user-permission.md) e um logon de usuário de banco de dados SQL Server

+ [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)

+ [Banco de dados de demonstração do NYC táxi](demo-data-nyctaxi-in-sql.md)

+ Um IDE do R, como RStudio ou a ferramenta RGUI interna incluída com R

É recomendável que você faça este passo a passos em uma estação de trabalho cliente. Você deve ser capaz de se conectar, na mesma rede, a um computador [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] com SQL Server e a linguagem R habilitada. Para obter instruções sobre a configuração da estação de trabalho, consulte [configurar um cliente de ciência de dados para o desenvolvimento de R](../r/set-up-a-data-science-client.md).

Como alternativa, você pode executar o Walkthrough em um computador que tenha [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e um ambiente de desenvolvimento de R, mas não recomendamos essa configuração para um ambiente de produção. Se você precisar colocar o cliente e o servidor no mesmo computador, certifique-se de instalar um segundo conjunto de bibliotecas do Microsoft R para enviar o script R de um cliente "remoto". Não use as bibliotecas de R que estão instaladas nos arquivos de programas da instância SQL Server. Especificamente, se você estiver usando um computador, precisará da biblioteca RevoScaleR em ambos os locais para dar suporte a operações de cliente e servidor.

+ C:\Arquivos de Files\Microsoft\R Client\R_SERVER\library\RevoScaleR 
+ C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library\RevoScaleR

> [!NOTE]
> Se você estiver usando [Machine Learning Server](https://docs.microsoft.com/machine-learning-server/) ou o [máquina virtual de ciência de dados](https://docs.microsoft.com/azure/machine-learning/data-science-virtual-machine/), em vez do cliente R, o caminho para RevoScaleR será C:\Program programas\microsoft\ml Server\R_SERVER\library\RevoScaleR

<a name="add-packages"></a>

## <a name="additional-r-packages"></a>Pacotes de R adicionais

Este tutorial requer várias bibliotecas de R que não são instaladas por padrão como parte do [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]. Você deve instalar os pacotes no cliente onde você desenvolve a solução e no computador [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] em que você implanta a solução.

### <a name="on-a-client-workstation"></a>Em uma estação de trabalho cliente

Em seu ambiente de R, copie as linhas a seguir e execute o código em uma janela de console (Rgui ou um IDE). Alguns pacotes também instalam os pacotes necessários. Em todos, cerca de 32 pacotes são instalados. Você deve ter uma conexão com a Internet para concluir esta etapa.
    
  ```R
  # Install required R libraries, if they are not already installed.
  if (!('ggmap' %in% rownames(installed.packages()))){install.packages('ggmap')}
  if (!('mapproj' %in% rownames(installed.packages()))){install.packages('mapproj')}
  if (!('ROCR' %in% rownames(installed.packages()))){install.packages('ROCR')}
  if (!('RODBC' %in% rownames(installed.packages()))){install.packages('RODBC')}
  ```

### <a name="on-the-server"></a>No servidor

Você tem várias opções para instalar pacotes no SQL Server. Por exemplo, SQL Server fornece o recurso de [Gerenciamento de pacotes do R](../r/install-additional-r-packages-on-sql-server.md) que permite que os administradores de banco de dados criem um repositório de pacotes e atribuam ao usuário os direitos para instalar seus próprios pacotes. No entanto, se você for um administrador no computador, poderá instalar novos pacotes usando o R, desde que você instale na biblioteca correta.

> [!NOTE]
> No **servidor, não** instale o em uma biblioteca de usuário, mesmo se solicitado. Se você instalar o em uma biblioteca de usuário, a instância de SQL Server não poderá localizar ou executar os pacotes. Para obter mais informações, consulte [instalando novos pacotes R no SQL Server](../r/install-additional-r-packages-on-sql-server.md).

1. No computador do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], abra RGui.exe **como administrador**.  Se você tiver instalado SQL Server R Services usando os padrões, o Rgui. exe poderá ser encontrado em C:\Arquivos de Programas\microsoft SQL Server\MSSQL13. MSSQLSERVER\R_SERVICES\bin\x64).

2. Em um prompt do R, execute os seguintes comandos do R:
  
  ```R
  install.packages("ggmap", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
  install.packages("mapproj", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
  install.packages("ROCR", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
  install.packages("RODBC", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
  ```
  Este exemplo usa a função grep R para pesquisar o vetor de caminhos disponíveis e encontrar o caminho que inclui "arquivos de programas". Para obter mais informações, consulte [https://www.rdocumentation.org/packages/base/functions/grep](https://www.rdocumentation.org/packages/base/functions/grep).

  Se você considerar que os pacotes já estão instalados, verifique a lista de pacotes instalados executando `installed.packages()`.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Explorar e resumir os dados](walkthrough-view-and-summarize-data-using-r.md)
