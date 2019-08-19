---
title: Como criar consultas MDX em R usando olapr
description: Use a biblioteca de pacotes olapr em SQL Server para gravar consultas MDX no script de linguagem R.
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/22/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: fb2918e5fb89d85d7f6fa1cc12622481e585d848
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68887671"
---
# <a name="how-to-create-mdx-queries-in-r-using-olapr"></a>Como criar consultas MDX em R usando olapr
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

O pacote [olapr](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) dá suporte a consultas MDX em cubos hospedados no SQL Server Analysis Services. Você pode criar uma consulta em um cubo existente, explorar dimensões e outros objetos de cubo e colar as consultas MDX existentes para recuperar dados.

Este artigo descreve os dois principais usos do pacote **olapr** :

+ [Criar uma consulta MDX a partir do R, usando os construtores fornecidos no pacote olapr](#buildMDX)
+ [Executar uma consulta MDX válida existente usando olapr e um provedor OLAP](#executeMDX)

Não há suporte para as seguintes operações:

+ Consultas DAX em um modelo de tabela
+ Criação de novos objetos OLAP
+ Write-back para partições, incluindo medidas ou somas

## <a name="buildMDX"></a>Criar uma consulta MDX do R

1. Defina uma cadeia de conexão que especifica a fonte de dados OLAP (instância do SSAS) e o provedor MSOLAP.

2. Use a função `OlapConnection(connectionString)` para criar um identificador para a consulta MDX e transmitir a cadeia de conexão.

3. Use o construtor `Query()` para instanciar um objeto de consulta.

4. Use as seguintes funções auxiliares para fornecer mais detalhes sobre as dimensões e medidas a serem incluídas na consulta MDX:

     + `cube()` Especifique o nome do banco de dados de SSAS. Se estiver se conectando a uma instância nomeada, forneça o nome da máquina e o nome da instância. 
     + `columns()`Forneça os nomes das medidas a serem usadas no argumento **em colunas** .
     + `rows()`Forneça os nomes das medidas a serem usadas no argumento **on Rows** .
     + `slicers()` Especifique um campo ou membros para usar como uma segmentação de dados. Uma segmentação de dados é como um filtro que é aplicado a todos os dados da consulta MDX.
     
     + `axis()` Especifique o nome de um eixo adicional para usar na consulta. 
     
         Um cubo OLAP pode conter até 128 eixos de consulta. Em geral, os quatro primeiros eixos são chamados de **colunas**, **linhas**, **páginas**e **capítulos**. 
         
         Se sua consulta for relativamente simples, você poderá usar as funções `columns`, `rows`, etc. para criar a consulta. No entanto, você também pode usar a função `axis()` com um valor de índice diferente de zero para criar uma consulta MDX com muitos qualificadores, ou para adicionar dimensões extras como qualificadores.

5. Passe o identificador e a consulta MDX concluída, em uma das funções a seguir, dependendo da forma dos resultados: 

  + `executeMD` Retorna uma matriz multidimensional
  + `execute2D` Retorna um quadro de dados (tabular) bidimensional

## <a name="executeMDX"></a>Executar uma consulta MDX válida do R

1. Defina uma cadeia de conexão que especifica a fonte de dados OLAP (instância do SSAS) e o provedor MSOLAP.

2. Use a função `OlapConnection(connectionString)` para criar um identificador para a consulta MDX e transmitir a cadeia de conexão.

3. Defina uma variável de R para armazenar o texto da consulta MDX.

4. Transmita o identificador e a variável que contendo a consulta MDX para as funções `executeMD` ou `execute2D`, dependendo da forma dos resultados.

    + `executeMD` Retorna uma matriz multidimensional
    + `execute2D` Retorna um quadro de dados (tabular) bidimensional

## <a name="examples"></a>Exemplos

Os exemplos a seguir baseiam-se no data mart AdventureWorks e no projeto de cubo, pois esse projeto está amplamente disponível, em várias versões, incluindo arquivos de backup que podem ser facilmente restaurados para Analysis Services. Se você não tiver um cubo existente, obtenha um exemplo de cubo usando uma destas opções:

+ Crie o cubo que é usado nestes exemplos seguindo o tutorial de Analysis Services até a lição 4: [Criando um cubo OLAP](https://docs.microsoft.com/analysis-services/multidimensional-tutorial/multidimensional-modeling-adventure-works-tutorial)

+ Baixe um cubo existente como um backup e restaure-o para uma instância do Analysis Services. Por exemplo, este site fornece um cubo totalmente processado no formato compactado: [Adventure Works modelo multidimensional SQL 2014](https://msftdbprodsamples.codeplex.com/downloads/get/882334). Extraia o arquivo e, em seguida, restaure-o para sua instância do SSAS. Para obter mais informações, consulte cmdlet [backup and Restore](https://docs.microsoft.com/analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases)ou [Restore-asdatabase](https://docs.microsoft.com/analysis-services/powershell/restore-asdatabase-cmdlet).

### <a name="1-basic-mdx-with-slicer"></a>1. MDX básica com segmentação de dados

Essa consulta MDX seleciona as _medidas_ para a contagem e o valor da contagem de vendas pela Internet e o valor das vendas e as coloca no eixo das Colunas. Ela adiciona um membro da dimensão SalesTerritory como uma *segmentação de dados*para filtrar a consulta de modo que somente as vendas da Austrália sejam usadas nos cálculos.

```MDX
SELECT {[Measures].[Internet Sales Count], [Measures].[InternetSales-Sales Amount]} ON COLUMNS, 
{[Product].[Product Line].[Product Line].MEMBERS} ON ROWS 
FROM [Analysis Services Tutorial] 
WHERE [Sales Territory].[Sales Territory Country].[Australia]
```

+ Nas colunas, você pode especificar várias medidas como elementos de uma cadeia de caracteres separada por vírgulas.
+ O eixo Linha usa todos os valores possíveis (todos os MEMBROS) da dimensão "Linha de produto". 
+ Essa consulta retornaria uma tabela com três colunas, contendo um Resumo acumulado de vendas pela Internet de todos os países.
+ A cláusula WHERE especifica o _eixo_da segmentação de os. Neste exemplo, a segmentação usa um membro da dimensão **SalesTerritory** para filtrar a consulta para que apenas as vendas da Austrália sejam usadas em cálculos.

#### <a name="to-build-this-query-using-the-functions-provided-in-olapr"></a>Para criar essa consulta usando as funções fornecidas em olapR

```R
cnnstr <- "Data Source=localhost; Provider=MSOLAP; initial catalog=Analysis Services Tutorial"
ocs <- OlapConnection(cnnstr)

qry <- Query()
cube(qry) <- "[Analysis Services Tutorial]"
columns(qry) <- c("[Measures].[Internet Sales Count]", "[Measures].[Internet Sales-Sales Amount]")
rows(qry) <- c("[Product].[Product Line].[Product Line].MEMBERS") 
slicers(qry) <- c("[Sales Territory].[Sales Territory Country].[Australia]")

result1 <- executeMD(ocs, qry)

```

Para uma instância nomeada, não se esqueça de escapar quaisquer caracteres que possam ser considerados caracteres de controle em R.  Por exemplo, a cadeia de conexão a seguir faz referência a uma instância OLAP01, em um servidor chamado ContosoHQ:

```R
cnnstr <- "Data Source=ContosoHQ\\OLAP01; Provider=MSOLAP; initial catalog=Analysis Services Tutorial"
```

#### <a name="to-run-this-query-as-a-predefined-mdx-string"></a>Para executar essa consulta como uma cadeia de caracteres MDX predefinida

```R
cnnstr <- "Data Source=localhost; Provider=MSOLAP; initial catalog=Analysis Services Tutorial"
ocs <- OlapConnection(cnnstr)

mdx <- "SELECT {[Measures].[Internet Sales Count], [Measures].[InternetSales-Sales Amount]} ON COLUMNS, {[Product].[Product Line].[Product Line].MEMBERS} ON ROWS FROM [Analysis Services Tutorial] WHERE [Sales Territory].[Sales Territory Country].[Australia]"

result2 <- execute2D(ocs, mdx)
```

Se você definir uma consulta usando o Construtor MDX no SQL Server Management Studio e, em seguida, salvar a cadeia de caracteres MDX, ela Numerará os eixos começando em 0, como mostrado aqui: 

```MDX
SELECT {[Measures].[Internet Sales Count], [Measures].[Internet Sales-Sales Amount]} ON AXIS(0), 
   {[Product].[Product Line].[Product Line].MEMBERS} ON AXIS(1) 
   FROM [Analysis Services Tutorial] 
   WHERE [Sales Territory].[Sales Territory Countr,y].[Australia]
```

Você ainda pode executar essa consulta como uma cadeia de caracteres MDX predefinida. No entanto, para criar a mesma consulta usando o `axis()` R usando a função, você deve renumerar os eixos começando em 1.

### <a name="2-explore-cubes-and-their-fields-on-an-ssas-instance"></a>2. Explore os cubos e seus campos em uma instância do SSAS

Você pode usar a função `explore` para retornar uma lista de cubos, dimensões ou membros para usar na construção de sua consulta. Isso é útil se você não tiver acesso a outras ferramentas de procura em OLAP ou se você quiser manipular programaticamente ou construir a consulta MDX.

#### <a name="to-list-the-cubes-available-on-the-specified-connection"></a>Para listar os cubos disponíveis na conexão especificada

Para exibir todos os cubos ou perspectivas na instância que você tem permissão para exibir, forneça o identificador como um argumento para `explore`.

> [!IMPORTANT]
> O resultado final **não** é um cubo; TRUE simplesmente indica que a operação de metadados foi bem-sucedida. Um erro será gerado se os argumentos forem inválidos.

```R
cnnstr <- "Data Source=localhost; Provider=MSOLAP; initial catalog=Analysis Services Tutorial"
ocs <- OlapConnection(cnnstr)
explore(ocs)
```

| Resultados  |
| ----|
| _Tutorial do Analysis Services_|
|_Vendas pela Internet_|
|_Vendas do revendedor_|
|_Resumo de vendas_|
|_[1] TRUE_|

#### <a name="to-get-a-list-of-cube-dimensions"></a>Para obter uma lista de dimensões do cubo

Para exibir todas as dimensões no cubo ou perspectiva, especifique o nome do cubo ou da perspectiva.

```R
cnnstr <- "Data Source=localhost; Provider=MSOLAP; initial catalog=Analysis Services Tutorial"
ocs \<- OlapConnection(cnnstr)
explore(ocs, "Sales")
```

| Resultados  |
| ----|
| _Cliente_|
|_Data_|
|_Região_|


#### <a name="to-return-all-members-of-the-specified-dimension-and-hierarchy"></a>Para retornar todos os membros da dimensão e hierarquia especificada

Depois de definir a fonte e criar o identificador, especifique o cubo, a dimensão e a hierarquia a serem retornados. Nos resultados de retorno, os itens que têm o prefixo **->** representam filhos do membro anterior.

```R
cnnstr <- "Data Source=localhost; Provider=MSOLAP; initial catalog=Analysis Services Tutorial"
ocs <- OlapConnection(cnnstr)
explore(ocs, "Analysis Services Tutorial", "Product", "Product Categories", "Category")
```

| Resultados  |
| ----|
| _Acessórios_|
|_Bicicletas_|
|_Roupas_|
|_Componentes_|
|-> Componentes do assembly|
|-> Componentes do assembly|


## <a name="see-also"></a>Confira também

[Usando dados de cubos OLAP em R](../../advanced-analytics/r/using-data-from-olap-cubes-in-r.md)
