---
title: Editor de loop foreach (página coleção) | Microsoft Docs
ms.custom: ''
ms.date: 08/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.foreachloopcontainer.collection.f1
ms.assetid: 95a19dde-61ca-4d9b-aa3d-131fa4264296
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 5b9396ab5a25bba979859ac685c4759b8b01c24d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66428804"
---
# <a name="foreach-loop-editor-collection-page"></a>Editor de Loop Foreach (página Coleção)
  Use a página **Coleção** da caixa de diálogo **Editor de Loop Foreach** para especificar o tipo de enumerador e configurá-lo.  
  
 Para saber mais sobre o contêiner Loop Foreach e como configurá-lo, consulte [Contêiner Loop Foreach](control-flow/foreach-loop-container.md) e [Configurar um contêiner Loop Foreach](../../2014/integration-services/configure-a-foreach-loop-container.md).  
  
## <a name="static-options"></a>Opções estáticas  
 **Enumera**  
 Selecione o tipo de enumerador na lista. As opções dessa propriedade são listadas na tabela a seguir.  
  
|Valor|DESCRIÇÃO|  
|-----------|-----------------|  
|**Enumerador de arquivo foreach**|Enumera arquivos. Se este valor for selecionado, serão exibidas as opções dinâmicas na seção **Enumerador de Arquivo Foreach**.|  
|**Enumerador de item foreach**|Enumera valores em um item. Se este valor for selecionado serão exibidas as opções dinâmicas na seção **Enumerador de Item Foreach**.|  
|**Enumerador ADO Foreach**|Enumera tabelas ou linhas em tabelas. Se este valor for selecionado serão exibidas as opções dinâmicas na seção **Enumerador ADO Foreach**.|  
|**Enumerador de conjunto de linhas de esquema foreach ADO.NET**|Enumera um esquema. Se este valor for selecionado serão exibidas as opções dinâmicas na seção **Enumerador ADO.NET Foreach**.|  
|**Enumerador foreach de variável**|Enumera o valor em uma variável. Se este valor for selecionado serão exibidas as opções dinâmicas na seção **Enumerador Foreach de Variável**.|  
|**Enumerador Nodelist Foreach**|Enumera nós em um documento XML. Se este valor for selecionado serão exibidas as opções dinâmicas na seção **Enumerador NodeList Foreach**.|  
|**Enumerador SMO foreach**|Enumera um objeto SMO. Se este valor for selecionado serão exibidas as opções dinâmicas na seção **Enumerador SMO Foreach**.|  
|**Enumerador de blob do Azure foreach**|Arquivos de Blob enumeráveis no local de Blob especificado. A seleção desse valor exibe as opções dinâmicas na seção **Enumerador de Blob do Azure Foreach**.|  
|**Enumerador de arquivo foreach ADLS**|Enumere arquivos em ADLS com filtros. Se esse valor for selecionado, serão exibidas as opções dinâmicas na seção **Enumerador de Arquivos ADLS Foreach**.|
  
 **Expressões**  
 Clique ou expanda **Expressões** para exibir a lista de expressões de propriedade existentes. Clique no botão de reticências **(...)** para adicionar uma expressão de propriedade para uma propriedade de enumerador ou edite e avalie uma expressão de propriedade existente.  
  
 **Tópicos relacionados:**  [Integration Services &#40;expressões&#41; SSIS](expressions/integration-services-ssis-expressions.md), [Editor de expressões de propriedade](expressions/property-expressions-editor.md), [Construtor de expressão](expressions/expression-builder.md)  
  
## <a name="enumerator-dynamic-options"></a>Opções dinâmicas do Enumerador  
  
### <a name="enumerator--foreach-file-enumerator"></a>Enumerador = Enumerador de Arquivo Foreach  
 Você usa o Enumerador de Arquivo Foreach para enumerar arquivos em uma pasta. Por exemplo, se o Loop Foreach incluir uma tarefa Execute SQL, você poderá usar o enumerador de arquivo Foreach para enumerar arquivos que contêm instruções SQL executadas pela tarefa Execute SQL. O enumerador pode ser configurado para incluir subpastas.  
  
 O conteúdo das pastas e subpastas que o enumerador de arquivo Foreach enumera pode alterar-se enquanto o loop estiver sendo executando porque processos externos ou tarefas no loop adicionam, renomeiam ou excluem arquivos enquanto o loop está em execução. Isso significa que podem acontecer várias situações inesperadas:  
  
-   Se forem excluídos arquivos, uma tarefa no Loop Foreach poderá executar o trabalho em um conjunto de arquivos diferente dos arquivos usados por tarefas subsequentes.  
  
-   Se forem renomeados arquivos e um processo externo adicionar arquivos automaticamente para substituir os arquivos renomeados, o Loop Foreach poderá executar o trabalho duas vezes no mesmo conteúdo de arquivo.  
  
-   Se forem adicionados arquivos, poderá ser difícil determinar para quais arquivos o Loop Foreach executou o trabalho.  
  
 **Pasta**  
 Forneça o caminho da pasta raiz a enumerar.  
  
 **Procurar**  
 Procure para localizar a pasta raiz.  
  
 **Arquivos**  
 Especifique os arquivos a enumerar.  
  
> [!NOTE]  
>  Use caracteres curinga (*) para especificar os arquivos a serem incluídos na coleção. Por exemplo, para incluir arquivos com nomes que contenham "abc", use o seguinte filtro: \*abc\*.  
>   
>  Quando você especifica uma extensão de nome de arquivo, o enumerador também retorna os arquivos que têm a mesma extensão com caracteres adicionais acrescentados. (É o mesmo comportamento do comando **dir** no sistema operacional, que também compara nomes de arquivos 8.3 para fins de compatibilidade com versões anteriores.) Este comportamento do enumerador poderia causar resultados inesperados. Por exemplo, você deseja enumerar somente arquivos do Excel 2003 e especifica "*.xls". Todavia, o enumerador também retornará arquivos do Excel 2007 porque esses arquivos têm a extensão ".xlsx".  
>   
>  Você pode usar uma expressão para especificar os arquivos a serem incluídos em uma coleção expandindo **Expressões** na página **Coleção**, selecionando a propriedade **FileSpec** e clicando no botão de reticências (…) para adicionar a expressão de propriedade. Para obter mais informações sobre a seleção dinâmica de arquivos especificados, consulte [SSIS-dynamic set File Mask: filespec](https://rajsudeep.blogspot.com/2010/09/ssisdynamically-set-file-mask-filespec.html)  
  
 **Totalmente qualificado**  
 Selecione para recuperar o caminho totalmente qualificado de nomes de arquivo. Se forem especificados caracteres curinga na opção Arquivos, os caminhos totalmente qualificados que retornarem corresponderão ao filtro.  
  
 **Somente nome**  
 Selecione para recuperar só os nomes de arquivo. Se forem especificados caracteres curinga na opção Arquivos, os nomes de arquivo que retornarem corresponderão ao filtro.  
  
 **Nome e extensão**  
 Selecione para recuperar os nomes de arquivo e suas extensões. Se forem especificados caracteres curinga na opção Arquivos, os nomes e extensões que retornarem corresponderão ao filtro.  
  
 **Desviar subpastas**  
 Selecione para incluir as subpastas na enumeração.  
  
### <a name="enumerator--foreach-item-enumerator"></a>Enumerador = Enumerador de Item Foreach  
 Use o Enumerador de Item Foreach para enumerar itens em uma coleção. Defina os itens na coleção especificando colunas e valores de coluna. As colunas em uma linha definem um item. Por exemplo, um item que especifica os executáveis que uma tarefa Execute Process executa e o diretório de trabalho usado pela tarefa tem duas colunas, uma que lista os nomes de executáveis e outra que lista o diretório de trabalho. O número de linhas determina o número de vezes que o loop é repetido. Se a tabela tiver 10 linhas, o loop será repetido 10 vezes.  
  
 Para atualizar as propriedades da tarefa Execute Process, mapeie variáveis para colunas de item usando o índice da coluna. A primeira coluna definida no item do enumerador tem o valor de índice 0, a segunda coluna, 1 e assim por diante. Os valores das variáveis são atualizados com cada repetição do loop. As propriedades do `Executable` e do `WorkingDirectory` da tarefa Execute Process podem então ser atualizadas por expressões de propriedade que usam estas variáveis.  
  
 **Definir os itens na coleção para cada item**  
 Forneça um valor para cada coluna na tabela.  
  
> [!NOTE]  
>  Uma linha nova é adicionada automaticamente à tabela depois que você insere valores nas colunas das linhas.  
  
> [!NOTE]  
>  Se os valores fornecidos não forem compatíveis com o tipo de dados da coluna, o texto aparecerá em vermelho.  
  
 **Tipo de dados de coluna**  
 Lista o tipo de dados da coluna ativa.  
  
 **Remover**  
 Selecione um item e clique em **Remover** para removê-lo da lista.  
  
 **Colunas**  
 Clique para configurar o tipo de dados das colunas no item.  
  
 **Tópicos relacionados:** [referência da interface do usuário da caixa de diálogo colunas de cada item](../../2014/integration-services/for-each-item-columns-dialog-box-ui-reference.md)  
  
### <a name="enumerator--foreach-ado-enumerator"></a>Enumerador = Enumerador ADO Foreach  
 Use o enumerador ADO Foreach para enumerar linhas ou tabelas em um objeto ADO ou ADO.NET armazenado em uma variável. Por exemplo, se o Loop Foreach incluir uma tarefa de Script que grava um conjunto de dados em uma variável, você poderá usar o enumerador ADO Foreach para enumerar linhas no conjunto de dados. Se a variável contiver um conjunto de dados ADO.NET, o enumerador poderá ser configurado para enumerar linhas em várias tabelas ou para enumerar tabelas.  
  
 **Variável de origem do objeto ADO**  
 Selecione uma variável definida pelo usuário na lista ou clique em \<**Nova variável...**> para criar uma nova variável.  
  
> [!NOTE]  
>  A variável deve ter o tipo de dados do Objeto, caso contrário ocorrerá um erro.  
  
 **Tópicos relacionados:** [Integration Services &#40;&#41; as variáveis do SSIS](integration-services-ssis-variables.md), [Adicionar variável](../../2014/integration-services/add-variable.md)  
  
 **Linhas na primeira tabela**  
 Selecione para enumerar somente linhas na primeira tabela.  
  
 **Linhas em todas as tabelas (somente conjunto de ADO.NET)**  
 Selecione para enumerar linhas em todas as tabelas. Esta opção só estará disponível se os objetos a enumerar forem todos membros do mesmo conjunto de dados ADO.NET.  
  
 **Todas as tabelas (somente conjunto de ADO.NET)**  
 Selecione para enumerar somente tabelas.  
  
### <a name="enumerator--foreach-adonet-schema-rowset-enumerator"></a>Enumerador = Enumerador de Conjunto de Linhas de Esquema ADO.NET Foreach  
 Use o Enumerador de Conjunto de Linhas de Esquema ADO.NET Foreach para enumerar um esquema para uma fonte de dados específica. Por exemplo, se o Loop Foreach incluir uma tarefa Execute SQL, você poderá usar o Enumerador de Conjunto de Linhas de Esquema ADO.NET Foreach para enumerar esquemas como as colunas no banco de dados **AdventureWorks** e a tarefa Execute SQL para obter as permissões do esquema.  
  
 **Conexão**  
 Selecione um gerenciador de conexões ADO.NET na lista ou clique em \<**Nova conexão...**> para criar um novo gerenciador de conexões ADO.NET.  
  
> [!IMPORTANT]  
>  O gerenciador de conexões ADO.NET deve usar um provedor .NET para OLE DB. Se você estiver se conectando com o SQL Server, o provedor indicado é o Cliente Nativo do [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , listado na seção **Provedores de .Net para OleDb** da caixa de diálogo **Gerenciador de conexões** .  
  
 **Tópicos relacionados:** [Gerenciador de conexões ADO](connection-manager/ado-connection-manager.md), [Configurar Gerenciador de conexões ADO.net](configure-ado-net-connection-manager.md)  
  
 **Esquema**  
 Selecione o esquema a enumerar.  
  
 **Definir restrições**  
 Defina as restrições a serem aplicadas ao esquema especificado.  
  
 **Tópicos relacionados:** [caixa de diálogo restrições de esquema](../../2014/integration-services/schema-restrictions-dialog-box.md)  
  
### <a name="enumerator--foreach-from-variable-enumerator"></a>Enumerador = Enumerador Foreach de Variável  
 Você usa o Enumerador Foreach de Variável para enumerar os objetos enumeráveis na variável especificada. Por exemplo, se o Loop Foreach incluir uma tarefa Execute SQL que executa uma consulta e armazena o resultado em uma variável, você poderá usar o Enumerador Foreach de Variável para enumerar os resultados da consulta.  
  
 **Variável**  
 Selecione uma variável na lista ou clique em \< **nova variável...**> para criar uma nova variável.  
  
 **Tópicos relacionados:** [Integration Services &#40;&#41; as variáveis do SSIS](integration-services-ssis-variables.md), [Adicionar variável](../../2014/integration-services/add-variable.md)  
  
### <a name="enumerator--foreach-nodelist-enumerator"></a>Enumerador = Enumerador NodeList Foreach  
 Use o enumerador NodeList Foreach para enumerar o conjunto de nós XML resultante da aplicação de uma expressão XPath a um arquivo XML. Por exemplo, se o Loop Foreach incluir uma tarefa Script, você poderá usar o enumerador NodeList Foreach para passar um valor que atende aos critérios da expressão XPath do arquivo XML para a tarefa Script.  
  
 A expressão XPath que se aplica ao arquivo XML é a operação XPath externa, armazenada na propriedade OuterXPathString. Se o tipo de enumeração XPath for definido `ElementCollection`como, o enumerador foreach NodeList poderá aplicar uma expressão XPath interna, armazenada na Propriedade InnerXPathString, a uma coleção de elemento.  
  
 Para saber mais sobre como trabalhar com documentos e dados XML, consulte "[Employing XML in the .NET Framework](https://go.microsoft.com/fwlink/?LinkId=56214)" na Biblioteca MSDN.  
  
 **DocumentSourceType**  
 Selecione o tipo de origem do documento XML. As opções dessa propriedade são listadas na tabela a seguir.  
  
|Valor|DESCRIÇÃO|  
|-----------|-----------------|  
|**Entrada direta**|Defina a origem de um documento XML.|  
|**Conexão de arquivo**|Selecione um arquivo que contém o documento XML.|  
|**Variável**|Defina a origem como uma variável que contém o documento XML.|  
  
 **Documentação**  
 Se **DocumentSourceType** estiver definido como **Entrada direta**, forneça o código XML ou clique no botão de reticências (...) para fornecer o XML usando a caixa de diálogo **Editor de Origem de Documento**.  
  
 Se **DocumentSourceType** for definido como **Conexão do arquivo**, selecione um Gerenciador de conexões do arquivo ou clique em \<**Nova conexão...**> para criar um novo gerenciador de conexões.  
  
 **Tópicos relacionados:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
 Se **DocumentSourceType** for definido como **Variável**, selecione uma variável existente ou clique em \<**Nova variável...**> para criar uma nova variável.  
  
 **Tópicos relacionados:** [Integration Services &#40;&#41; as variáveis do SSIS](integration-services-ssis-variables.md), [adicione a variável](../../2014/integration-services/add-variable.md).  
  
 **EnumerationType**  
 Selecione um tipo de enumeração na lista. As opções dessa propriedade são listadas na tabela a seguir.  
  
|Valor|DESCRIÇÃO|  
|-----------|-----------------|  
|**Navegador**|Enumere usando um XPathNavigator.|  
|**Nó**|Enumere nós retornados por uma operação XPath.|  
|**NodeText**|Enumere nós de texto retornados por uma operação XPath.|  
|`ElementCollection`|Enumera nós de elementos retornados por uma operação XPath.|  
  
 **OuterXPathStringSourceType**  
 Selecione o tipo de origem da cadeia XPath. As opções dessa propriedade são listadas na tabela a seguir.  
  
|Valor|DESCRIÇÃO|  
|-----------|-----------------|  
|**Entrada direta**|Defina a origem de um documento XML.|  
|**Conexão de arquivo**|Selecione um arquivo que contém o documento XML.|  
|**Variável**|Defina a origem como uma variável que contém o documento XML.|  
  
 `OuterXPathString`  
 Se **OuterXPathStringSourceType** for definido como **Entrada direta**, forneça a cadeia de caracteres XPath.  
  
 Se **OuterXPathStringSourceType** for definido como **Conexão do arquivo**, selecione um Gerenciador de conexões do arquivo ou clique em \<**Nova conexão...**> para criar um novo gerenciador de conexões.  
  
 **Tópicos relacionados:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
 Se **OuterXPathStringSourceType** for definido como **Variável**, selecione uma variável existente ou clique em \<**Nova variável...**> para criar uma nova variável.  
  
 **Tópicos relacionados:** [Integration Services &#40;&#41; as variáveis do SSIS](integration-services-ssis-variables.md), [adicione a variável](../../2014/integration-services/add-variable.md).  
  
 **InnerElementType**  
 Se **EnumerationType** for definido como `ElementCollection`, selecione o tipo de elemento interno na lista.  
  
 **InnerXPathStringSourceType**  
 Seleciona o tipo de origem da cadeia interna XPath. As opções dessa propriedade são listadas na tabela a seguir.  
  
|Valor|DESCRIÇÃO|  
|-----------|-----------------|  
|**Entrada direta**|Defina a origem de um documento XML.|  
|**Conexão de arquivo**|Selecione um arquivo que contém o documento XML.|  
|**Variável**|Defina a origem como uma variável que contém o documento XML.|  
  
 `InnerXPathString`  
 Se **InnerXPathStringSourceType** for definido como **Entrada direta**, forneça a cadeia de caracteres XPath.  
  
 Se **InnerXPathStringSourceType** for definido como **Conexão do arquivo**, selecione um Gerenciador de conexões do arquivo ou clique em \<**Nova conexão...**> para criar um novo gerenciador de conexões.  
  
 **Tópicos relacionados:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
 Se **InnerXPathStringSourceType** for definido como **Variável**, selecione uma variável existente ou clique em \<**Nova variável...**> para criar uma nova variável.  
  
 **Tópicos relacionados:** [Integration Services &#40;&#41; as variáveis do SSIS](integration-services-ssis-variables.md), [adicione a variável](../../2014/integration-services/add-variable.md).  
  
### <a name="enumerator--foreach-smo-enumerator"></a>Enumerador = Enumerador SMO Foreach  
 Use o enumerador SMO Foreach para enumerar objetos SMO (SQL Server Management Object). Por exemplo, se o Loop Foreach incluir uma tarefa Execute SQL, você poderá usar o enumerador SMO Foreach para enumerar as tabelas no banco de dados **AdventureWorks** e executar consultas que contam o número de linhas em cada tabela.  
  
 **Conexão**  
 Selecione um gerenciador de conexões ADO.NET existente ou clique em \<**Nova conexão...**> para criar um novo gerenciador de conexões.  
  
 Tópicos relacionados: [ADO.NET Connection Manager](connection-manager/ado-net-connection-manager.md), [Configure ADO.NET Connection Manager](configure-ado-net-connection-manager.md)  
  
 **Enumera**  
 Especifique o objeto SMO a enumerar.  
  
 **Procurar**  
 Selecione a enumeração SMO.  
  
 **Tópicos relacionados:** [selecionar a caixa de diálogo enumeração do Smo](../../2014/integration-services/select-smo-enumeration-dialog-box.md)  
  
### <a name="enumerator--foreach-azure-blob-enumerator"></a>Enumerador = Enumerador de Blob do Azure Foreach  
 O  **Enumerador de Blob do Azure**permite que um pacote do SSIS enumere arquivos de Blob no local de Blob especificado. O nome do arquivo de blob enumerado pode ser armazenado em uma variável e usado em tarefas dentro do Contêiner do Loop Foreach.  
  
 **Gerenciador de conexões do armazenamento do Azure**  
 Selecione um Gerenciador de Conexão de Armazenamento do Azure existente ou crie um novo que se refere a uma Conta de Armazenamento do Azure.  
  
 Tópicos Relacionados: [Azure Storage Connection Manager](connection-manager/azure-storage-connection-manager.md).  
  
 **Nome do contêiner de BLOB**  
 Especifique o nome do contêiner de Blob que contém os arquivos de Blob a serem enumerados.  
  
 **Diretório de BLOB**  
 Especifique o diretório de Blob que contém os arquivos de Blob a serem enumerados. O diretório de blob é uma estrutura hierárquica virtual.  
  
 **Filtro de nome de BLOB**  
 Especifique um filtro de nome para enumerar arquivos com determinado padrão de nome. Por ex.: MySheet*.xls\* incluirá arquivos como MySheet001.xls e MySheetABC.xlsx.  
  
 **Intervalo de tempo de blob de/para filtrar**  
 Especifique um filtro de intervalo de tempo. Arquivos modificados após **TimeRangeFrom** e antes de **TimeRangeTo** serão enumerados.  
### <a name="enumerator--foreach-adls-file-enumerator"></a> Enumerador = Enumerador de Arquivos ADLS Foreach  
O **enumerador de arquivo ADLS** permite que um pacote do SSIS enumere arquivos no ADLS com filtros. O caminho completo`/`de barra () prefixado de arquivos enumerados pode ser armazenado em uma variável e usado em tarefas dentro do contêiner Loop Foreach.
  
**AzureDataLakeConnection**  
Especifica um gerenciador de conexões do Azure Data Lake ou cria um novo que se refere a uma conta do ADLS.   
  
**AzureDataLakeDirectory**  
Especifica o diretório ADLS a ser pesquisado.
  
**FileNamePattern**  
Especifica um filtro de nome de arquivo. Somente os arquivos cujo nome corresponde ao padrão especificado serão enumerados. Curingas `*` e `?` são compatíveis. 
  
**SearchRecursively**  
Especifica se deve-se pesquisar recursivamente dentro do diretório especificado.  
  
## <a name="external-resources"></a>Recursos externos  
  
-   Entrada de blog, [SSIS For Each Node List Enumerator](https://go.microsoft.com/fwlink/?LinkId=220671), em bidn.com.  
  
-   Entrada de blog, [SSIS – definir dinamicamente a máscara de arquivo: filespec](https://rajsudeep.blogspot.com/2010/09/ssisdynamically-set-file-mask-filespec.html).  
  
## <a name="see-also"></a>Consulte Também  
 [Referência de mensagens e erros do Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Editor de loop foreach &#40;página Geral&#41;](general-page-of-integration-services-designers-options.md)   
 [Editor de loop foreach &#40;página Mapeamentos de variáveis&#41;](../../2014/integration-services/foreach-loop-editor-variable-mappings-page.md)   
 [Página Expressões](expressions/expressions-page.md)   
 [Contêiner Loop For](control-flow/for-loop-container.md)  
  
  
