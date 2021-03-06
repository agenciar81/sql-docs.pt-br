---
title: 'SQL Server 2014: hardware & requisitos de software'
ms.custom: ''
ms.date: 07/10/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- Setup [SQL Server], software
- software [SQL Server]
- installing SQL Server, software
- operating systems [SQL Server], SQL Server requirements
- Setup [SQL Server], cross-language support
- operating systems [SQL Server], cross-language support
- network connections [SQL Server], requirements
- disk space [SQL Server], SQL Server installations
- WOW [SQL Server]
- Setup [SQL Server], hardware
- dependencies [SQL Server], SQL Server installations
- cluster hardware requirements [SQL Server]
- endpoints [SQL Server], SQL Server installations
- Internet [SQL Server], SQL Server installations
- hardware [SQL Server]
- Windows on Windows [SQL Server]
- installing SQL Server, hardware
- Setup Configuration Checker
- SCC [SQL Server]
- operating systems [SQL Server]
- space [SQL Server], SQL Server installations
- system configuration checker
- installing SQL Server, cross-language support
- Internet [SQL Server]
- space [SQL Server]
- extended system support [SQL Server]
- 64-bit edition [SQL Server]
- failover clustering [SQL Server]
- failover clustering [SQL Server], hardware requirements
- 32-bit edition [SQL Server]
- locales [SQL Server], SQL Server installations
- cross-language support
- disk space [SQL Server]
- localized SQL Server versions
ms.assetid: 09bcf20b-0a40-4131-907f-b61479d5e4d8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 664422d0875ade408e48166920852ee66162a885
ms.sourcegitcommit: 976a246a92bd6d1665882484a3f49a6d3edd2b8b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79433813"
---
# <a name="sql-server-2014-hardware-and-software-requirements"></a>SQL Server 2014: requisitos de hardware e software

 > - Experimente o SQL Server 2016 instalando a ** [edição gratuita do Developer](https://my.visualstudio.com/Downloads?q=SQL%20Server%20Developer).**  
  
## <a name="considerations"></a>Considerações 
  
-   É recomendável [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] executar em computadores com o formato de arquivo NTFS. O sistema de arquivos FAT32 tem suporte, mas não é recomendado, pois é menos seguro do que o sistema de arquivos NTFS.  
  
-   Não é possível instalar o em unidades somente leitura, mapeadas ou compactadas.  
  
-   Para permitir que o componente do Visual Studio seja instalado [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] corretamente, o requer que você instale uma atualização. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]A instalação verifica a presença dessa atualização e, em seguida, exige que você baixe e instale essa atualização antes de poder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] continuar a instalação. Para evitar a interrupção durante [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a instalação, baixe e instale a atualização **antes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] executar a instalação** , conforme descrito abaixo (ou instale todas as atualizações do .net 3,5 SP1 disponíveis no Windows Update):  
  
    -   Para [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] o SP2, obtenha a atualização necessária [aqui](https://go.microsoft.com/fwlink/?LinkId=198093).  
  
    -   Para qualquer outro sistema operacional com suporte, essa atualização é incluída.  
  
-   Não há suporte para a iniciação da Instalação do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] por meio do Cliente dos Serviços de Terminal. A instalação falhará se você iniciar a instalação por meio do cliente dos serviços de terminal.   
  
-   A Instalação do[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instala os seguintes componentes de software necessários ao produto:  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Arquivos de suporte à instalação  
  
-   Para obter os requisitos mínimos [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de [!INCLUDE[win8srv](../../includes/win8srv-md.md)] versão [!INCLUDE[win8](../../includes/win8-md.md)]a serem instalados no ou no, consulte [instalando o SQL Server no Windows Server 2012 ou no Windows 8](https://support.microsoft.com/kb/2681562) (https://support.microsoft.com/kb/2681562).  
  
 Este tópico contém as seguintes seções:  
  
-   [Requisitos de hardware e software](hardware-and-software-requirements-for-installing-sql-server.md#hwswr)  
  
-   [Requisitos de processador, memória e sistema operacional](hardware-and-software-requirements-for-installing-sql-server.md#pmosr)  
  
-   [Suporte entre idiomas](hardware-and-software-requirements-for-installing-sql-server.md#CrossLanguageSupport)  
  
-   [Suporte a sistema estendido](hardware-and-software-requirements-for-installing-sql-server.md#ess)  
  
-   [Requisitos de espaço em disco rígido (32 bits e 64 bits)](hardware-and-software-requirements-for-installing-sql-server.md#HardDiskSpace)  
  
-   [Tipos de armazenamento para arquivos de dados](hardware-and-software-requirements-for-installing-sql-server.md#StorageTypes)  
  
-   [Instalando o SQL Server em um controlador de domínio](hardware-and-software-requirements-for-installing-sql-server.md#DC_support)  
  
##  <a name="hwswr"></a> Requisitos de Hardware e Software  


A tabela nesta seção lista os requisitos mínimos para executar o SQL Server. Também há opções de configuração recomendadas para o [desempenho ideal](https://support.microsoft.com/help/2964518). 

Os seguintes requisitos de software se aplicam a todas as instalações:  

  
|Componente|Requisito|  
|---------------|-----------------|  
|.NET Framework|O .NET 3.5 SP1 é um requisito para [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] quando você seleciona [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)], [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)], replicação, ou [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], e ele não é mais instalado pela instalação do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . <br />-Se você executar a instalação e não tiver o .NET 3,5 SP1, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a instalação exigirá que você baixe e instale o .net 3,5 SP1 para poder continuar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] com a instalação. (Instale o .NET 3,5 SP1 do [Microsoft .NET Framework 3,5 Service Pack 1](https://www.microsoft.com/download/details.aspx?id=22).) A mensagem de erro inclui um link para o centro de download ou você pode baixar o .NET 3,5 SP1 do Windows Update. Para evitar a interrupção durante a Instalação do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , você pode baixar e instalar o .NET 3.5 SP1 antes de executar a Instalação do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .<br />-Se você executar a instalação em um computador [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] com o [!INCLUDE[win8](../../includes/win8-md.md)]SP1 ou, deverá habilitar o .NET Framework 3,5 SP1 antes [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]de instalar o.<br />-Se não houver acesso à Internet, você deverá baixar e instalar o .NET Framework 3,5 SP1 antes de executar a instalação para instalar qualquer um dos componentes mencionados acima. Para obter mais informações sobre as recomendações e diretrizes sobre como adquirir e habilitar o .NET Framework 3,5 [!INCLUDE[win8](../../includes/win8-md.md)] no [!INCLUDE[win8srv](../../includes/win8srv-md.md)]e no, consulte considerações de implantação dohttps://msdn.microsoft.com/library/windows/hardware/hh975396) [Microsoft .NET Framework 3,5](https://msdn.microsoft.com/library/windows/hardware/hh975396) (.<br /><br /> O .NET 4.0 é um requisito do [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. O [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instala o .NET 4.0 durante a etapa de instalação de recurso.<br />-Se você estiver instalando [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] as edições do, verifique se uma conexão com a Internet está disponível no computador. A Instalação do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] baixa e instala o .NET Framework 4 porque ele não está incluído na mídia do [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].<br />-[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]não instala o .NET 4,0 no modo Server Core do [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 ou. [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Você deve instalar o .NET 4.0 antes de instalar o [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] em uma instalação Server Core do [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 ou [!INCLUDE[win8srv](../../includes/win8srv-md.md)].|  
|Windows PowerShell|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]não instala ou habilita o Windows PowerShell 2,0; no entanto, o Windows PowerShell 2,0 é [!INCLUDE[ssDE](../../includes/ssde-md.md)] um pré-requisito [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]de instalação para componentes do e do. Se a Instalação relatar que o Windows PowerShell 2.0 não está presente, você poderá instalá-lo ou habilitá-lo seguindo as instruções na página do [Windows Management Framework](https://go.microsoft.com/fwlink/?LinkId=186214) .|  
|Software de rede|Os sistemas operacionais com suporte para [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] têm software de rede interno. As instâncias nomeadas e padrão de uma instalação autônoma dão suporte aos seguintes protocolos de rede: memória compartilhada, pipes nomeados, TCP/IP e VIA.<br /><br /> Observação: o protocolo VIA não tem suporte em clusters de failover. Os clientes ou aplicativos em execução no mesmo nó do cluster de failover que a instância do SQL Server podem usar o protocolo de Memória Compartilhada para se conectar ao SQL Server usando seu endereço de pipe local. No entanto, esse tipo de conexão não tem reconhecimento de cluster e falhará após um failover da instância. Portanto, ela não é recomendada e só deve ser usada em cenários muito específicos. O protocolo VIA foi preterido. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]<br /><br /> Para obter mais informações sobre protocolos de rede e bibliotecas de rede, consulte [Network Protocols and Network Libraries](network-protocols-and-network-libraries.md).|  
|Virtualização|O [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tem suporte em ambientes de máquina virtual em execução na função Hyper-V em:<br />-<br />                    
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 edições Standard, Enterprise e Datacenter<br />-[!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]SP1 Standard, Enterprise e Datacenter Editions.<br />-<br />                    [!INCLUDE[win8srv](../../includes/win8srv-md.md)]Datacenter e Standard Editions.<br /><br /> Além dos recursos exigidos pela partição pai, cada máquina virtual (partição filho) deve ter recursos de processador, memória e recursos de disco suficientes para sua instância do [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Os requisitos são listados posteriormente neste tópico.\*<br /><br /> Na função de Hyper-V no [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 ou [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1, no máximo quatro processadores virtuais podem ser alocados para máquinas virtuais que executam as edições do [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 32 bits/64 bits ou [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 64 bits ou [!INCLUDE[win8srv](../../includes/win8srv-md.md)] 64 bits.<br /><br /> Na função de Hyper-V no [!INCLUDE[win8srv](../../includes/win8srv-md.md)]:<br />No máximo 8 (oito) processadores virtuais podem ser alocados para máquinas virtuais que estão executando o [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 32 bits/64 bits.<br />No máximo 64 (sessenta e quatro) processadores virtuais podem ser alocados para máquinas virtuais que executam o [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 de 64 bits ou as edições de 64 bits do [!INCLUDE[win8srv](../../includes/win8srv-md.md)] .<br /><br /> Para obter mais informações sobre limites de capacidade de computação para edições diferentes do [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e como elas podem diferir em ambientes físicos e virtualizados com processadores hyper-threaded, consulte [Compute Capacity Limits by Edition of SQL Server](../compute-capacity-limits-by-edition-of-sql-server.md). Para obter mais informações sobre a função Hyper-V, consulte o [site do Windows Server 2008](https://go.microsoft.com/fwlink/?LinkId=182820)<br /><br /> ** \* Importante \* \* ** O clustering de failover de convidado [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]tem suporte no. Para obter mais informações sobre as versões do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que têm suporte e sobre os sistemas operacionais para clustering de failover convidado, bem como sobre o suporte para virtualização, consulte [Política de suporte para produtos do Microsoft SQL Server que estiver executando em um ambiente de virtualização de hardware](https://go.microsoft.com/fwlink/?LinkId=151676).|  
|Disco rígido|O[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] requer no mínimo 6 GB de espaço disponível no disco rígido.<br /><br /> Os requisitos de espaço em disco variam de acordo com os componentes do [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] instalados. Para obter mais informações, consulte [Hard Disk Space Requirements (32-Bit and 64 Bit)](hardware-and-software-requirements-for-installing-sql-server.md#HardDiskSpace) , posteriormente neste tópico. Para obter mais informações sobre tipos de armazenamento de arquivos de dados com suporte, consulte [Tipos de armazenamento para arquivos de dados](hardware-and-software-requirements-for-installing-sql-server.md#StorageTypes).|  
|Unidade|É necessária uma unidade de DVD, conforme apropriado, para a instalação a partir de disco.|  
|Monitoramento|O[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] requer um monitor com resolução Super-VGA (800 x 600) ou superior.|  
|Internet|A funcionalidade de Internet requer acesso à Internet (a cobrança de taxas poderá ser aplicável).|  
  
 * A [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] execução em uma máquina virtual será mais lenta do que a execução nativa devido à sobrecarga da virtualização.  
  
##  <a name="pmosr"></a> Requisitos de processador, de memória e do sistema operacional  
 Os requisitos de memória e processador a seguir aplicam-se a todas as edições do [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]:  
  
|Componente|Requisito|  
|---------------|-----------------|  
|Memória<sup>[1]</sup>|**Mínimo:**<br /><br /> Edições Express: 512 MB<br /><br /> Todas as outras edições: 1 GB<br /><br /> **Recomendado:**<br /><br /> Edições Express: 1 GB<br /><br /> Todas as outras edições: Pelo menos 4 GB e deve ser aumentado à medida que o tamanho do banco de dados aumenta para garantir um ótimo desempenho.|  
|Velocidade do processador|**Mínimo:**<br /><br /> Processador x86: 1,0 GHz<br /><br /> Processador x64: 1,4 GHz<br /><br /> **Recomendado:** 2,0 GHz ou mais rápido|  
|Tipo de processador|Processador x64: AMD Opteron, AMD Athlon 64, Intel Xeon com suporte Intel EM64T, Intel Pentium IV com suporte EM64T<br /><br /> Processador x86: Processador compatível com Pentium III ou mais rápido|  
  
 <sup>[1]</sup> A memória mínima necessária para instalar o [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] componente no [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) é 2 GB de RAM, que é diferente do requisito [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mínimo de memória. Para obter informações sobre como instalar o DQS, consulte [Install Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md).  
  
 **Suporte a WOW64:**  
  
 O WOW64 (Windows de 32 bits no Windows de 64 bits) é um recurso de edições de 64 bits do Windows que permite que aplicativos de 32 bits sejam executados nativamente no modo de 32 bits. Os aplicativos funcionam no modo de 32 bits mesmo que o sistema operacional subjacente esteja em execução em um sistema operacional de 64 bits.  
  
-   Em um sistema operacional de 64 bits com suporte, a edição de 32 bits do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pode ser instalada no subsistema de 32 bits do WOW64 de um servidor de 64 bits. O WOW64 tem suporte somente para instâncias autônomas do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Não há suporte para o WOW64 em instalações de cluster de failover do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Para instalações da edição de 64 bits do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] em sistemas operacionais com suporte para 64 bits, as Ferramentas de Gerenciamento têm suporte no WOW64. Para obter mais informações sobre sistemas operacionais com suporte, selecione uma edição do [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] nas seções abaixo.  
  
 **Suporte do Server Core:**  

 Agora [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] é compatível com a instalação do Server Core do Windows Server 2008 R2, do Windows Server 2012, do Windows Server 2012 R2, do Windows Server 2016 e do Windows Server 2019. 

A instalação do [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] no Server Core é compatível com as seguintes edições do Windows Server:

|                              |                                |
| :------------------------    | :------------------------------|
| Windows Server 2019 Standard | Windows Server 2019 Datacenter |
| Windows Server 2016 Standard | Windows Server 2016 Datacenter |
| Windows Server 2012 R2 Standard | Windows Server 2012 R2  Datacenter|
| Windows Server 2012 Standard | Windows Server 2012 Datacenter |
| Windows Server 2008 R2 SP1 Standard | Windows Server 2008 R2 SP1 Datacenter |
| Windows Server 2008 R2 SP1 Enterprise | Windows Server 2008 R2 SP1 Web|
   | &nbsp; | &nbsp; |
  
 Para obter mais informações sobre [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] como instalar o no Server Core, consulte [instalar o SQL Server 2014 no Server Core](../../database-engine/install-windows/install-sql-server-on-server-core.md).  
  
   >[!NOTE]
   > As edições do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] com suporte no [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] 64 bits x64 Standard também têm suporte no [!INCLUDE[sbs_2](../../includes/sbs-2-md.md)] 64 bits x64.  
  
 **Suporte do sistema operacional:**  
  
 As edições do [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] são classificadas da seguinte maneira:  
  
-   [Principais edições do SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md#TOP_Principal)  
  
-   [Edições especializadas do SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md#TOP_SP)  
  
-   [Edições de amplitude do SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md#TOP_Breadth)  
  
###  <a name="TOP_Principal"></a>Requisitos de sistemas operacionais das edições principais  
 A tabela a seguir mostra os requisitos de sistema operacional para as edições principais do [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]:  
  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Versão|32 bits|64 bits|  
|---------------------------------------|-------------|-------------|  
|[!INCLUDE[ssEnterprise](../../includes/ssenterprise-md.md)]|[!INCLUDE[winserver2019_datacenter_md](../../includes/winserver2019-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2019_standard_md](../../includes/winserver2019-standard-md.md)]<br/><br/>[!INCLUDE[winserver2016_datacenter_md](../../includes/winserver2016-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2016_standard_md](../../includes/winserver2016-standard-md.md)]<br/><br/>
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Standard 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Essentials 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Foundation 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Datacenter 64 bits<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)]Padrão de 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Essentials 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Foundation 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Enterprise 64 bits<br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]SP1 Standard 64-bit<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Web 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Enterprise 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Standard 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Web 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Enterprise 32 bits<br /><br /> [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)]SP2 Standard 32-bit<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Web 32 bits|[!INCLUDE[winserver2019_datacenter_md](../../includes/winserver2019-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2019_standard_md](../../includes/winserver2019-standard-md.md)]<br/><br/>[!INCLUDE[winserver2016_datacenter_md](../../includes/winserver2016-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2016_standard_md](../../includes/winserver2016-standard-md.md)]<br/><br/>
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Standard 64 bits<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)]R2 Essentials 64-bit<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Foundation 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Datacenter 64 bits<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)]Padrão de 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Essentials 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Foundation 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Enterprise 64 bits<br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]SP1 Standard 64-bit<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Web 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Enterprise 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Standard 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Web 64 bits|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Business Intelligence|[!INCLUDE[winserver2019_datacenter_md](../../includes/winserver2019-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2019_standard_md](../../includes/winserver2019-standard-md.md)]<br/><br/>[!INCLUDE[winserver2016_datacenter_md](../../includes/winserver2016-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2016_standard_md](../../includes/winserver2016-standard-md.md)]<br/><br/>
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Standard 64 bits<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)]R2 Essentials 64-bit<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Foundation 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Datacenter 64 bits<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)]Padrão de 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Essentials 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Foundation 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Enterprise 64 bits<br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]SP1 Standard 64-bit<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Web 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Enterprise 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Standard 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Web 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Enterprise 32 bits<br /><br /> [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)]SP2 Standard 32-bit<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Web 32 bits|[!INCLUDE[winserver2019_datacenter_md](../../includes/winserver2019-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2019_standard_md](../../includes/winserver2019-standard-md.md)]<br/><br/>[!INCLUDE[winserver2016_datacenter_md](../../includes/winserver2016-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2016_standard_md](../../includes/winserver2016-standard-md.md)]<br/><br/>
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Standard 64 bits<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)]R2 Essentials 64-bit<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Foundation 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Datacenter 64 bits<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)]Padrão de 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Essentials 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Foundation 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Enterprise 64 bits<br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]SP1 Standard 64-bit<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Web 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Enterprise 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Standard 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Web 64 bits|  
|[!INCLUDE[ssStandard](../../includes/ssstandard-md.md)]|Windows 10 Home 64 bits<br /><br /> Windows 10 Professional 64 bits<br /><br /> Windows 10 Enterprise 64 bits<br /><br /> Windows 10 Home 32 bits<br /><br /> Windows 10 Professional 32 bits<br /><br /> Windows 10 Enterprise 32 bits<br /><br />[!INCLUDE[winserver2019_datacenter_md](../../includes/winserver2019-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2019_standard_md](../../includes/winserver2019-standard-md.md)]<br/><br/>[!INCLUDE[winserver2016_datacenter_md](../../includes/winserver2016-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2016_standard_md](../../includes/winserver2016-standard-md.md)]<br/><br/> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Standard 64 bits<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)]R2 Essentials 64-bit<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Foundation 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Datacenter 64 bits<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)]Padrão de 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Essentials 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Foundation 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Enterprise 64 bits<br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]SP1 Standard 64-bit<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Foundation 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Web 64 bits<br /><br /> [!INCLUDE[winblue_client_2](../../includes/winblue-client-2-md.md)]32 bits<br /><br /> [!INCLUDE[winblue_client_pro_2](../../includes/winblue-client-pro-2-md.md)]32 bits<br /><br /> [!INCLUDE[winblue_client_ent_2](../../includes/winblue-client-ent-2-md.md)]32 bits<br /><br /> [!INCLUDE[winblue_client_2](../../includes/winblue-client-2-md.md)]64 bits<br /><br /> [!INCLUDE[winblue_client_pro_2](../../includes/winblue-client-pro-2-md.md)]64 bits<br /><br /> [!INCLUDE[winblue_client_ent_2](../../includes/winblue-client-ent-2-md.md)]64 bits<br /><br /> [!INCLUDE[win8](../../includes/win8-md.md)]32 bits<br /><br /> [!INCLUDE[win8_client_pro_2](../../includes/win8-client-pro-2-md.md)]32 bits<br /><br /> [!INCLUDE[win8_client_ent_2](../../includes/win8-client-ent-2-md.md)]32 bits<br /><br /> [!INCLUDE[win8](../../includes/win8-md.md)]64 bits<br /><br /> [!INCLUDE[win8_client_pro_2](../../includes/win8-client-pro-2-md.md)]64 bits<br /><br /> [!INCLUDE[win8_client_ent_2](../../includes/win8-client-ent-2-md.md)]64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Ultimate 64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Enterprise 64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Professional 64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Ultimate 32 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Enterprise 32 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Professional 32 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Enterprise 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Standard 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Foundation 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Web 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Enterprise 32 bits<br /><br /> [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)]SP2 Standard 32-bit<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Web 32 bits|Windows 10 Home 64 bits<br /><br /> Windows 10 Professional 64 bits<br /><br /> Windows 10 Enterprise 64 bits<br /><br />[!INCLUDE[winserver2019_datacenter_md](../../includes/winserver2019-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2019_standard_md](../../includes/winserver2019-standard-md.md)]<br/><br/>[!INCLUDE[winserver2016_datacenter_md](../../includes/winserver2016-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2016_standard_md](../../includes/winserver2016-standard-md.md)]<br/><br/>
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Standard 64 bits<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)]R2 Essentials 64-bit<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Foundation 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Datacenter 64 bits<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)]Padrão de 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Essentials 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Foundation 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Enterprise 64 bits<br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]SP1 Standard 64-bit<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Foundation 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Web 64 bits<br /><br /> [!INCLUDE[winblue_client_2](../../includes/winblue-client-2-md.md)]64 bits<br /><br /> [!INCLUDE[winblue_client_pro_2](../../includes/winblue-client-pro-2-md.md)]64 bits<br /><br /> [!INCLUDE[winblue_client_ent_2](../../includes/winblue-client-ent-2-md.md)]64 bits<br /><br /> [!INCLUDE[win8](../../includes/win8-md.md)]64 bits<br /><br /> [!INCLUDE[win8_client_pro_2](../../includes/win8-client-pro-2-md.md)]64 bits<br /><br /> [!INCLUDE[win8_client_ent_2](../../includes/win8-client-ent-2-md.md)]64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Ultimate 64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Enterprise 64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Professional 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Enterprise 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Standard 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Foundation 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Web 64 bits| 
  
###  <a name="TOP_SP"></a>Requisitos do sistema operacional das edições especializadas  
 A tabela a seguir mostra os requisitos de sistema operacional para as edições especializadas do [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]:  
  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Versão|32 bits|64 bits|  
|---------------------------------------|-------------|-------------|  
|[!INCLUDE[ssWeb](../../includes/ssweb-md.md)]|Windows 10 Home 64 bits<br /><br /> Windows 10 Professional 64 bits<br /><br /> Windows 10 Enterprise 64 bits<br /><br /> Windows 10 Home 32 bits<br /><br /> Windows 10 Professional 32 bits<br /><br /> Windows 10 Enterprise 32 bits<br /><br />[!INCLUDE[winserver2019_datacenter_md](../../includes/winserver2019-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2019_standard_md](../../includes/winserver2019-standard-md.md)]<br/><br/>[!INCLUDE[winserver2016_datacenter_md](../../includes/winserver2016-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2016_standard_md](../../includes/winserver2016-standard-md.md)]<br/><br/>
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Standard 64 bits<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)]R2 Essentials 64-bit<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Foundation 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Datacenter 64 bits<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)]Padrão de 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Essentials 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Foundation 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Enterprise 64 bits<br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]SP1 Standard 64-bit<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Web 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Enterprise 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Standard 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Web 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Enterprise 32 bits<br /><br /> [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)]SP2 Standard 32-bit<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Web 32 bits|Windows 10 Home 64 bits<br /><br /> Windows 10 Professional 64 bits<br /><br /> Windows 10 Enterprise 64 bits<br /><br />[!INCLUDE[winserver2019_datacenter_md](../../includes/winserver2019-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2019_standard_md](../../includes/winserver2019-standard-md.md)]<br/><br/>[!INCLUDE[winserver2016_datacenter_md](../../includes/winserver2016-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2016_standard_md](../../includes/winserver2016-standard-md.md)]<br/><br/>
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Datacenter 64 bits<br /><br />
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Standard 64 bits<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)]R2 Essentials 64-bit<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Foundation 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Datacenter 64 bits<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)]Padrão de 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Essentials 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Foundation 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Enterprise 64 bits<br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]SP1 Standard 64-bit<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Web 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Enterprise 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Standard 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Web 64 bits| 
  
###  <a name="TOP_Breadth"></a>Requisitos do sistema operacional das edições de amplitude
 A tabela a seguir mostra os requisitos de sistema operacional para as edições de amplitude do [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]:  
  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Versão|32 bits|64 bits|  
|---------------------------------------|-------------|-------------|  
|[!INCLUDE[ssDeveloper](../../includes/ssdeveloper-md.md)]|Windows 10 Home 64 bits<br /><br /> Windows 10 Professional 64 bits<br /><br /> Windows 10 Enterprise 64 bits<br /><br /> Windows 10 Home 32 bits<br /><br /> Windows 10 Professional 32 bits<br /><br /> Windows 10 Enterprise 32 bits<br /><br />[!INCLUDE[winserver2019_datacenter_md](../../includes/winserver2019-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2019_standard_md](../../includes/winserver2019-standard-md.md)]<br/><br/>[!INCLUDE[winserver2016_datacenter_md](../../includes/winserver2016-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2016_standard_md](../../includes/winserver2016-standard-md.md)]<br/><br/>
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Datacenter 64 bits<br /><br />
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Standard 64 bits<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)]R2 Essentials 64-bit<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Foundation 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Datacenter 64 bits<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)]Padrão de 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Essentials 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Foundation 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Enterprise 64 bits<br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]SP1 Standard 64-bit<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Web 64 bits<br /><br /> [!INCLUDE[winblue_client_2](../../includes/winblue-client-2-md.md)]32 bits<br /><br /> [!INCLUDE[winblue_client_pro_2](../../includes/winblue-client-pro-2-md.md)]32 bits<br /><br /> [!INCLUDE[winblue_client_ent_2](../../includes/winblue-client-ent-2-md.md)]32 bits<br /><br /> [!INCLUDE[winblue_client_2](../../includes/winblue-client-2-md.md)]64 bits<br /><br /> [!INCLUDE[winblue_client_pro_2](../../includes/winblue-client-pro-2-md.md)]64 bits<br /><br /> [!INCLUDE[winblue_client_ent_2](../../includes/winblue-client-ent-2-md.md)]64 bits<br /><br /> [!INCLUDE[win8](../../includes/win8-md.md)]32 bits<br /><br /> [!INCLUDE[win8_client_pro_2](../../includes/win8-client-pro-2-md.md)]32 bits<br /><br /> [!INCLUDE[win8_client_ent_2](../../includes/win8-client-ent-2-md.md)]32 bits<br /><br /> [!INCLUDE[win8](../../includes/win8-md.md)]64 bits<br /><br /> [!INCLUDE[win8_client_pro_2](../../includes/win8-client-pro-2-md.md)]64 bits<br /><br /> [!INCLUDE[win8_client_ent_2](../../includes/win8-client-ent-2-md.md)]64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Ultimate 64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Enterprise 64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Professional 64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Home Premium 64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Home Basic 64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Ultimate 32 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Enterprise 32 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Professional 32 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Home Premium 32 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Home Basic 32 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Enterprise 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Standard 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Web 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Enterprise 32 bits<br /><br /> [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)]SP2 Standard 32-bit<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Web 32 bits|Windows 10 Home 64 bits<br /><br /> Windows 10 Professional 64 bits<br /><br /> Windows 10 Enterprise 64 bits<br /><br />[!INCLUDE[winserver2019_datacenter_md](../../includes/winserver2019-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2019_standard_md](../../includes/winserver2019-standard-md.md)]<br/><br/>[!INCLUDE[winserver2016_datacenter_md](../../includes/winserver2016-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2016_standard_md](../../includes/winserver2016-standard-md.md)]<br/><br/>
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Datacenter 64 bits<br /><br />
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Standard 64 bits<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)]R2 Essentials 64-bit<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Foundation 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Datacenter 64 bits<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)]Padrão de 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Essentials 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Foundation 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Enterprise 64 bits<br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]SP1 Standard 64-bit<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Web 64 bits<br /><br /> [!INCLUDE[winblue_client_2](../../includes/winblue-client-2-md.md)]64 bits<br /><br /> [!INCLUDE[winblue_client_pro_2](../../includes/winblue-client-pro-2-md.md)]64 bits<br /><br /> [!INCLUDE[winblue_client_ent_2](../../includes/winblue-client-ent-2-md.md)]64 bits<br /><br /> [!INCLUDE[win8](../../includes/win8-md.md)]64 bits<br /><br /> [!INCLUDE[win8_client_pro_2](../../includes/win8-client-pro-2-md.md)]64 bits<br /><br /> [!INCLUDE[win8_client_ent_2](../../includes/win8-client-ent-2-md.md)]64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Ultimate 64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Enterprise 64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Professional 64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Home Premium 64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Home Basic 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Enterprise 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Standard 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Web 64 bits|  
|[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]|Windows 10 Home 64 bits<br /><br /> Windows 10 Professional 64 bits<br /><br /> Windows 10 Enterprise 64 bits<br /><br /> Windows 10 Home 32 bits<br /><br /> Windows 10 Professional 32 bits<br /><br /> Windows 10 Enterprise 32 bits<br /><br />[!INCLUDE[winserver2019_datacenter_md](../../includes/winserver2019-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2019_standard_md](../../includes/winserver2019-standard-md.md)]<br/><br/>[!INCLUDE[winserver2016_datacenter_md](../../includes/winserver2016-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2016_standard_md](../../includes/winserver2016-standard-md.md)]<br/><br/>
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Standard 64 bits<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)]R2 Essentials 64-bit<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Foundation 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Datacenter 64 bits<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)]Padrão de 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Essentials 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Foundation 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Enterprise 64 bits<br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]SP1 Standard 64-bit<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Foundation 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Web 64 bits<br /><br /> [!INCLUDE[winblue_client_2](../../includes/winblue-client-2-md.md)]32 bits<br /><br /> [!INCLUDE[winblue_client_pro_2](../../includes/winblue-client-pro-2-md.md)]32 bits<br /><br /> [!INCLUDE[winblue_client_ent_2](../../includes/winblue-client-ent-2-md.md)]32 bits<br /><br /> [!INCLUDE[winblue_client_2](../../includes/winblue-client-2-md.md)]64 bits<br /><br /> [!INCLUDE[winblue_client_pro_2](../../includes/winblue-client-pro-2-md.md)]64 bits<br /><br /> [!INCLUDE[winblue_client_ent_2](../../includes/winblue-client-ent-2-md.md)]64 bits<br /><br /> [!INCLUDE[win8](../../includes/win8-md.md)]32 bits<br /><br /> [!INCLUDE[win8_client_pro_2](../../includes/win8-client-pro-2-md.md)]32 bits<br /><br /> [!INCLUDE[win8_client_ent_2](../../includes/win8-client-ent-2-md.md)]32 bits<br /><br /> [!INCLUDE[win8](../../includes/win8-md.md)]64 bits<br /><br /> [!INCLUDE[win8_client_pro_2](../../includes/win8-client-pro-2-md.md)]64 bits<br /><br /> [!INCLUDE[win8_client_ent_2](../../includes/win8-client-ent-2-md.md)]64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Ultimate 64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Enterprise 64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Professional 64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Home Premium 64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Home Basic 64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Ultimate 32 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Enterprise 32 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Professional 32 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Home Premium 32 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Home Basic 32 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Enterprise 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Standard 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Foundation 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Web 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Enterprise 32 bits<br /><br /> [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)]SP2 Standard 32-bit<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Web 32 bits|Windows 10 Home 64 bits<br /><br /> Windows 10 Professional 64 bits<br /><br /> Windows 10 Enterprise 64 bits<br /><br />[!INCLUDE[winserver2019_datacenter_md](../../includes/winserver2019-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2019_standard_md](../../includes/winserver2019-standard-md.md)]<br/><br/>[!INCLUDE[winserver2016_datacenter_md](../../includes/winserver2016-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2016_standard_md](../../includes/winserver2016-standard-md.md)]<br/><br/>
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Standard 64 bits<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)]R2 Essentials 64-bit<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Foundation 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Datacenter 64 bits<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)]Padrão de 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Essentials 64 bits<br /><br /> 
  [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Foundation 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Enterprise 64 bits<br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]SP1 Standard 64-bit<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Foundation 64 bits<br /><br /> 
  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 Web 64 bits<br /><br /> [!INCLUDE[winblue_client_2](../../includes/winblue-client-2-md.md)]64 bits<br /><br /> [!INCLUDE[winblue_client_pro_2](../../includes/winblue-client-pro-2-md.md)]64 bits<br /><br /> [!INCLUDE[winblue_client_ent_2](../../includes/winblue-client-ent-2-md.md)]64 bits<br /><br /> [!INCLUDE[win8](../../includes/win8-md.md)]64 bits<br /><br /> [!INCLUDE[win8_client_pro_2](../../includes/win8-client-pro-2-md.md)]64 bits<br /><br /> [!INCLUDE[win8_client_ent_2](../../includes/win8-client-ent-2-md.md)]64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Ultimate 64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Enterprise 64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Professional 64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Home Premium 64 bits<br /><br /> 
  [!INCLUDE[win7](../../includes/win7-md.md)] SP1 Home Basic 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Datacenter 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Enterprise 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Standard 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Foundation 64 bits<br /><br /> 
  [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] SP2 Web 64 bits|  
  
## <a name="minimum-sql-server-version-requirements-for-windows-10"></a>Requisitos mínimos de versão do SQL Server para Windows 10  
 Antes de instalar o SQL Server em um computador executando o Windows 10, certifique-se de que você atende aos seguintes requisitos mínimos:  
  
-   Para o SQL Server 2014, você deve aplicar o SQL Server 2014 Service Pack 1 ou outra atualização mais recente. Para obter mais informações, consulte [Como obter o service pack mais recente para o SQL Server 2014](https://support.microsoft.com/kb/2958069).  
  
-   Para o SQL Server 2012, você deve aplicar o SQL Server 2012 Service Pack 2 ou outra atualização mais recente. Para obter mais informações, consulte [Como obter o service pack mais recente para o SQL Server 2012](https://support.microsoft.com/kb/2755533).  
  
-   SQL Server 2008 R2  
    e não há suporte para o SQL Server 2008 no Windows 10.  
  
##  <a name="CrossLanguageSupport"></a> Suporte em qualquer idioma  
 Para obter mais informações sobre o suporte em vários idiomas e as considerações sobre a instalação do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] em idiomas localizados, consulte [Versões de idiomas locais no SQL Server](local-language-versions-in-sql-server.md).  
  
##  <a name="ess"></a>Suporte ao sistema estendido  
 As versões de 64 bits do [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] incluem o suporte para sistemas estendidos, também conhecidos como WOW64 (Windows de 32 bits no Windows de 64 bits). O WOW64 é um recurso de edições de 64 bits do Windows que permite que aplicativos de 32 bits sejam executados nativamente no modo de 32 bits. Os aplicativos funcionam no modo de 32 bits mesmo que o sistema operacional subjacente esteja em execução no sistema operacional de 64 bits.  
  
##  <a name="HardDiskSpace"></a>Requisitos de espaço em disco rígido (32 bits e 64 bits)  
 Durante a instalação Windows Installer cria arquivos temporários na unidade do sistema. Antes de executar a instalação para instalar ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]atualizar, verifique se você tem pelo menos **6,0 GB** de espaço em disco disponível na unidade do sistema para esses arquivos. Esse requisito se aplica mesmo se você instalar componentes em uma unidade não padrão.  
  
 Os requisitos reais de espaço em disco dependem da configuração do seu sistema e dos recursos que decidir instalar. Para obter uma lista dos recursos com suporte nas edições [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]do, consulte [recursos com suporte nas edições do SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md). A tabela a seguir fornece os requisitos de espaço em disco para componentes do [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .  
  
|**Recurso**|**Requisito de espaço em disco**|  
|-----------------|--------------------------------|  
|O[!INCLUDE[ssDE](../../includes/ssde-md.md)] e arquivos de dados, Replicação, Pesquisa de Texto Completo e Data Quality Services|811 MB|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] e arquivos de dados|345 MB|  
|O [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] e o Gerenciador de Relatórios|304 MB|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|591 MB|  
|[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]|243 MB|  
|Componentes cliente (exceto os componentes dos Manuais Online do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e as ferramentas do Integration Services)|1823 MB|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Componentes dos manuais online para exibir e gerenciar o conteúdo da ajuda<sup>1</sup>|375 KB|  
  
 <sup>1</sup> O requisito de espaço em disco para o conteúdo dos Manuais Online baixado é de 200 MB.  
  
##  <a name="StorageTypes"></a> Tipos de armazenamento de arquivos de dados  
 Os tipos de armazenamento de arquivos de dados com suporte são:  
  
-   Disco local  
  
-   Armazenamento compartilhado  
  
-   Compartilhamento de arquivos SMB  
  
    > **Observação:**  O armazenamento SMB não tem suporte [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] para arquivos de dados para instalações autônomas ou clusterizadas. Em vez disso, use o armazenamento anexado direto ou a rede de área de armazenamento.  
  
    > **IMPORTANTE:** O armazenamento SMB pode ser hospedado por um servidor de arquivos do Windows ou por um dispositivo de armazenamento SMB de terceiros. Se o servidor de arquivos do Windows for usado, sua versão deve ser 2008 ou posterior. Para obter mais informações sobre como instalar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usando um compartilhamento de arquivos SMB como uma opção de armazenamento, consulte [Instalar o SQL Server com o compartilhamento de arquivos SMB como uma opção de armazenamento](../../database-engine/install-windows/install-sql-server-with-smb-fileshare-as-a-storage-option.md).  
  
    > **AVISO!**  A instalação de cluster de failover do[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] só dá suporte a Disco Local para a instalação de arquivos tempdb. Verifique se o caminho especificado para os arquivos de dados e de log do tempdb é válido em **todos** os nós de cluster. Durante o failover, se os diretórios tempdb não estiverem disponíveis no nó do destino de failover, o recurso do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] não ficará online.  
  
##  <a name="DC_support"></a>Instalando [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] em um controlador de domínio-limitações  
 Por motivos de segurança, é recomendável não instalar o [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] em um controlador de domínio. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] não bloqueará a instalação em um computador que seja um controlador de domínio, mas as seguintes limitações se aplicam:  
  
-   Você não pode executar os serviços do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] em um controlador de domínio sob uma conta de serviço local.  
  
-   Depois que o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for instalado em um computador, você não poderá alterar o computador de um membro do domínio para um controlador de domínio. Você deve desinstalar o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] antes de alterar o computador host para um controlador de domínio.  
  
-   Depois que o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for instalado em um computador, você não poderá alterar o computador de um controlador de domínio para um membro do domínio. Você deve desinstalar o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] antes de alterar o computador host para um membro do domínio.  
  
-   Não há suporte às instâncias de cluster de failover do[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] em que os nós de agrupamento sejam controladores de domínio.  
  
-   A Instalação do[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] não pode criar grupos de segurança ou provisionar contas de serviço do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] em um controlador de domínio somente leitura. Nesse cenário, haverá falha na Instalação.  
  
## <a name="see-also"></a>Consulte Também  
 [Planejando uma instalação do SQL Server](planning-a-sql-server-installation.md)   
 [Considerações sobre segurança para uma instalação do SQL Server](security-considerations-for-a-sql-server-installation.md)   
 [Especificações do produto SQL Server 2014](../../getting-started/sql-server-2014-product-specifications.md)  
