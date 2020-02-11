---
title: Propriedades personalizadas de transformação | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Aggregate transformation [Integration Services]
- Slowly Changing Dimension transformation
- Import Column transformation [Integration Services]
- Sort transformation
- Unpivot transformation
- Merge Join transformation
- Data Mining Query transformation
- Fuzzy Grouping transformation
- Data Conversion transformation
- Fuzzy Lookup transformation
- Term Extraction transformation
- Row Count transformation custom properties [Integration Services]
- transformations [Integration Services], properties
- Pivot transformation
- Lookup transformation
- Percentage Sampling transformation
- Export Column transformation [Integration Services]
- Row Sampling transformation
- Conditional Split transformation custom properties [Integration Services]
- custom properties [Integration Services]
- Audit transformation
- Term Lookup transformation
- Script Component transformation custom properties [Integration Services]
- Derived Column transformation
- OLE DB Command transformation
- Copy Column transformation custom properties [Integration Services]
- Character Map transformation custom properties [Integration Services]
ms.assetid: 56f5df6a-56f6-43df-bca9-08476a3bd931
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 1a3e999975f13654a5f3c2f34a2325324c5a36ac
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62770662"
---
# <a name="transformation-custom-properties"></a>Propriedades personalizadas da transformação
  Além das propriedades que são comuns à maioria dos objetos de fluxo de dados no [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] modelo de objeto, muitos objetos de fluxo de dados têm propriedades personalizadas que são específicas para o objeto. Essas propriedades personalizadas estão disponíveis somente em tempo de execução e não constam da Documentação de Referência de Programação Gerenciada do [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] .  
  
 Este tópico lista e descreve as propriedades personalizadas de várias transformações de fluxo de dados. Para obter mais informações sobre as propriedades comuns à maioria dos objetos Data Flow, consulte [Common Properties](../../common-properties.md).  
  
 É possível definir algumas propriedades de transformações usando expressões de propriedade. Para obter mais informações, consulte [Propriedades de fluxo de dados que podem ser definidas usando expressões](../../data-flow-properties-that-can-be-set-by-using-expressions.md).  
  
## <a name="transformations-with-custom-properties"></a>Transformações com propriedades personalizadas  
  
||||  
|-|-|-|  
|[Tais](#aggregate)|[Exportar Coluna](#extract)|[Contagem de Linhas](#rowcount)|  
|[Auditoria](#audit)|[Agrupamento Difuso](#fgroup)|[Amostragem de linha](#rowsamp)|  
|[transformação Cache](#cachetransform)|[Pesquisa Difusa](#flookup)|[Componente Script](#script)|  
|[Mapa de Caracteres](#charmap)|[Importar Coluna](#insert)|[Dimensão de Alteração Lenta](#scd)|  
|[Divisão Condicional](#condsplit)|[Pesquisa](#lookup)|[Classificar](#sort)|  
|[Copiar Coluna](#copymap)|[Junção de Mesclagem](#mjoin)|[Extração de termos](#textract)|  
|[Conversão de Dados](#dataconv)|[OLE DB comando](#oledbcmd)|[Pesquisa de Termos](#tlookup)|  
|[Consulta de mineração de dados](#dmquery)|[Amostragem percentual](#percent)|[Não Dinâmico](#unpivot)|  
|[Coluna Derivada](#derived)|[Dinâmico](#pivot)||  
  
### <a name="transformations-without-custom-properties"></a>Transformações sem propriedades personalizadas  
 As transformações a seguir não têm nenhuma propriedade personalizada nos níveis do componente, da entrada ou da saída: [Merge Transformation](merge-transformation.md), [Multicast Transformation](multicast-transformation.md)e [Union All Transformation](union-all-transformation.md). Somente as propriedades comuns a todos os componentes de fluxo de dados são usadas.  
  
##  <a name="aggregate"></a>Propriedades personalizadas da transformação Agregação  
 A transformação Agregação tem as propriedades personalizadas e as propriedades comuns a todos os componentes de fluxo de dados.  
  
 A tabela a seguir descreve as propriedades personalizadas da transformação Agregação. Todas as propriedades são de leitura/gravação.  
  
|Propriedade|Tipo de dados|DESCRIÇÃO|  
|--------------|---------------|-----------------|  
|AutoExtendFactor|Integer|Um valor entre 1 e 100 que especifica a porcentagem para a extensão da memória durante a agregação. O valor padrão dessa propriedade é **25**.|  
|CountDistinctKeys|Integer|Um valor que especifica o número exato de contagens diferentes que a agregação pode gravar. Se um valor de CountDistinctScale for especificado, o valor em CountDistinctKeys terá precedência.|  
|CountDistinctScale|Inteiro (enumeração)|Um valor que descreve o número aproximado de valores distintos em uma coluna que a agregação pode contar. Essa propriedade pode ter um dos seguintes valores:<br /><br /> **Baixo** (1)-indica até 500.000 valores de chave<br /><br /> **Médio** (2)-indica até 5 milhões valores de chave<br /><br /> **Alta** (3)-indica mais de 25 milhões valores de chave.<br /><br /> Não **especificado** (0)-indica que nenhum valor de CountDistinctScale é usado. O uso da opção **Não Especificado** (0) pode afetar o desempenho em grandes conjuntos de dados.|  
|simétricas|Integer|Um valor que especifica o número exato de chaves Agrupar por que a agregação pode gravar. Se um valor de KeyScalevalue for especificado, o valor em Keys terá preferência.|  
|KeyScale|Inteiro (enumeração)|Um valor que descreve aproximadamente quantos valores de chave Agrupar por podem ser gravados pela agregação. Essa propriedade pode ter um dos seguintes valores:<br /><br /> **Baixo** (1)-indica até 500.000 valores de chave.<br /><br /> **Médio** (2)-indica até 5 milhões valores de chave.<br /><br /> **Alta** (3)-indica mais de 25 milhões valores de chave.<br /><br /> Não **especificado** (0) – indica que nenhum valor de KeyScale é usado.|  
  
 A tabela a seguir descreve as propriedades personalizadas da saída da transformação Agregação. Todas as propriedades são de leitura/gravação.  
  
|Propriedade|Tipo de dados|DESCRIÇÃO|  
|--------------|---------------|-----------------|  
|simétricas|Integer|Um valor que especifica o número exato de chaves Agrupar por que pode ser gravado pela agregação. Se um valor de KeyScale for especificado, o valor em Keys terá preferência.|  
|KeyScale|Inteiro (enumeração)|Um valor que descreve aproximadamente quantos valores de chave Agrupar por podem ser gravados pela agregação. Essa propriedade pode ter um dos seguintes valores:<br /><br /> **Baixo** (1)-indica até 500.000 valores de chave,<br /><br /> **Médio** (2)-indica até 5 milhões valores de chave,<br /><br /> **Alta** (3)-indica mais de 25 milhões valores de chave.<br /><br /> Não **especificado** (0)-indica que nenhum valor de KeyScale é usado.|  
  
 A tabela a seguir descreve as propriedades personalizadas das colunas de saída da transformação Agregação. Todas as propriedades são de leitura/gravação.  
  
|Propriedade|Tipo de dados|DESCRIÇÃO|  
|--------------|---------------|-----------------|  
|AggregationColumnId|Integer|O `LineageID` de uma coluna que participa de GROUP BY ou funções de agregação.|  
|AggregationComparisonFlags|Integer|Um valor que especifica como a transformação Agregação compara dados de cadeia de caracteres em uma coluna. Para obter mais informações, consulte [Comparing String Data](../comparing-string-data.md).|  
|AggregationType|Inteiro (enumeração)|Um valor que especifica a operação de agregação a ser executada na coluna. Essa propriedade pode ter um dos seguintes valores:<br /><br /> **Contagem** (1)<br /><br /> **Contar tudo** (2)<br /><br /> **CountDistinct** (3)<br /><br /> **Sum** (4)<br /><br /> **Média** (5)<br /><br /> **Máximo** (7)<br /><br /> **Mínimo** (6)<br /><br /> **Agrupar por** (0)|  
|CountDistinctKeys|Integer|Quando o tipo de agregação é **Contar distintos**, um valor que especifica o número exato de chaves que a agregação pode gravar. Se um valor de CountDistinctScale for especificado, o valor em CountDistinctKeys terá precedência.|  
|CountDistinctScale|Inteiro (enumeração)|Quando o tipo de agregação é **Contar distintos**, um valor que especifica o número aproximado de valores de chave que podem ser gravados pela agregação. Essa propriedade pode ter um dos seguintes valores:<br /><br /> **Baixo** (1)-indica até 500.000 valores de chave,<br /><br /> **Médio** (2)-indica até 5 milhões valores de chave,<br /><br /> **Alta** (3)-indica mais de 25 milhões valores de chave.<br /><br /> Não **especificado** (0)-indica que nenhum valor de CountDistinctScale é usado.|  
|IsBig|Boolean|Um valor que indica se a coluna contém um valor superior a 4 bilhões ou com mais precisão que um valor de precisão dupla de ponto flutuante. O valor pode ser 0 ou 1. 0 indica que IsBig é `False` e a coluna não contém um valor grande ou precisa. O valor padrão desta propriedade é 1.|  
  
 A entrada e as colunas de entrada da transformação Agregação não têm nenhuma propriedade personalizada.  
  
 Para obter mais informações, consulte [Aggregate Transformation](aggregate-transformation.md).  
  
##  <a name="audit"></a>Propriedades personalizadas da transformação Auditoria  
 A transformação Auditoria só tem as propriedades comuns a todos os componentes de fluxo de dados no nível do componente.  
  
 A tabela a seguir descreve as propriedades personalizadas das colunas de saída da transformação Auditoria. Todas as propriedades são de leitura/gravação.  
  
|Nome da propriedade|Tipo de dados|DESCRIÇÃO|  
|-------------------|---------------|-----------------|  
|LineageItemSelected|Inteiro (enumeração)|O item de auditoria selecionado para saída. Essa propriedade pode ter um dos seguintes valores:<br /><br /> **GUID da instância de execução** (0)<br /><br /> **Hora de início da execução** (4)<br /><br /> **Nome do computador** (5)<br /><br /> **ID do pacote** (1)<br /><br /> **Nome do pacote** (2)<br /><br /> **ID da tarefa** (8)<br /><br /> **Nome da tarefa** (7)<br /><br /> **Nome de usuário** (6)<br /><br /> **ID da versão** (3)|  
  
 A entrada, as colunas de entrada e a saída da transformação Auditoria não têm nenhuma propriedade personalizada.  
  
 Para obter mais informações, consulte [Audit Transformation](audit-transformation.md).  
  
##  <a name="cachetransform"></a>Propriedades personalizadas da transformação transformação de cache  
 A transformação Cache tem as propriedades personalizadas e as propriedades comuns a todos os componentes de fluxo de dados.  
  
 A tabela a seguir descreve as propriedades da transformação Cache. Todas as propriedades são de leitura/gravação.  
  
|Propriedade|Tipo de dados|DESCRIÇÃO|  
|--------------|---------------|-----------------|  
|ConnectionManager|String|Especifica o nome do gerenciador de conexões.|  
|ValidateExternalMetadata|Boolean|Indica se a transformação Cache é validada usando fontes de dados externas no momento de design. Se a propriedade for definida como `False`, a validação das fontes de dados externas acontecerá em tempo de execução.<br /><br /> O valor padrão é `True`.|  
|AvailableInputColumns|String|Lista as colunas de entrada disponíveis.|  
|InputColumns|String|Lista das colunas de entrada selecionadas.|  
|CacheColumnName|String|Especifica o nome da coluna mapeada para uma coluna de entrada selecionada.<br /><br /> É necessário que o nome da coluna na propriedade CacheColumnName corresponda ao nome da coluna correspondente listada na página **Colunas** do **Editor do Gerenciador de Conexões do Cache**.<br /><br /> Para obter mais informações, consulte [cache Connection Manager editor](../../cache-connection-manager-editor.md)|  
  
##  <a name="charmap"></a>Propriedades personalizadas da transformação mapa de caracteres  
 A transformação Mapa de Caracteres só tem as propriedades comuns a todos os componentes de fluxo de dados no nível do componente.  
  
 A tabela a seguir descreve as propriedades personalizadas das colunas de saída da transformação Mapa de Caracteres. Todas as propriedades são de leitura/gravação.  
  
|Propriedade|Tipo de dados|DESCRIÇÃO|  
|--------------|---------------|-----------------|  
|InputColumnLineageId|Integer|Um valor que especifica o `LineageID` da coluna de entrada que é a fonte da coluna de saída.|  
|MapFlags|Inteiro (enumeração)|Um valor que especifica as operações de cadeia de caracteres que a transformação Mapa de Caracteres executa na coluna. Essa propriedade pode ter um dos seguintes valores:<br /><br /> **Estorno de bytes** (2)<br /><br /> **Largura total** (6)<br /><br /> **Meia largura** (5)<br /><br /> **Hiragana** (3)<br /><br /> **Katakana** (4)<br /><br /> **Capitalização linguística** (7)<br /><br /> **Minúsculas** (0)<br /><br /> **Chinês simplificado** (8)<br /><br /> **Chinês tradicional**(9)<br /><br /> **Letras maiúsculas** (1)|  
  
 A entrada, as colunas de entrada e a saída da transformação Mapa de Caracteres não têm nenhuma propriedade personalizada.  
  
 Para obter mais informações, consulte [Character Map Transformation](character-map-transformation.md).  
  
##  <a name="condsplit"></a>Propriedades personalizadas da transformação Divisão condicional  
 A transformação Divisão Condicional só tem as propriedades comuns a todos os componentes de fluxo de dados no nível do componente.  
  
 A tabela a seguir descreve as propriedades personalizadas da saída da transformação Divisão Condicional. Todas as propriedades são de leitura/gravação.  
  
|Propriedade|Tipo de dados|DESCRIÇÃO|  
|--------------|---------------|-----------------|  
|EvaluationOrder|Integer|Um valor que especifica a posição de uma condição, associado a uma saída, na lista de condições avaliada pela transformação Divisão Condicional. As condições são avaliadas do valor mais baixo para o valor mais alto.|  
|Expression|String|Uma expressão que representa a condição avaliada pela transformação Divisão Condicional. Colunas são representadas por identificadores de linhagem.|  
|FriendlyExpression|String|Uma expressão que representa a condição avaliada pela transformação Divisão Condicional. Colunas são representadas pelos nomes.<br /><br /> O valor dessa propriedade pode ser especificado com uma expressão de propriedades.|  
|IsDefaultOut|Boolean|Um valor que indica se a saída é a saída padrão.|  
  
 A entrada, as colunas de entrada e as colunas de saída da transformação Divisão Condicional não têm nenhuma propriedade personalizada.  
  
 Para obter mais informações, consulte [Conditional Split Transformation](conditional-split-transformation.md).  
  
##  <a name="copymap"></a>Propriedades personalizadas da transformação copiar coluna  
 A transformação Copiar Coluna só tem as propriedades comuns a todos os componentes de fluxo de dados no nível do componente.  
  
 A tabela a seguir descreve as propriedades personalizadas das colunas de saída da transformação Copiar Coluna. Todas as propriedades são de leitura/gravação.  
  
|Nome da propriedade|Tipo de dados|DESCRIÇÃO|  
|-------------------|---------------|-----------------|  
|copyColumnId|Integer|O `LineageID` da coluna de entrada da qual a coluna de saída é copiada.|  
  
 A entrada, as colunas de entrada e a saída da transformação Copiar Coluna não têm nenhuma propriedade personalizada.  
  
 Para obter mais informações, consulte [Copy Column Transformation](copy-column-transformation.md).  
  
##  <a name="dataconv"></a>Propriedades personalizadas da transformação conversão de dados  
 A transformação Conversão de Dados só tem as propriedades comuns a todos os componentes de fluxo de dados no nível do componente.  
  
 A tabela a seguir descreve as propriedades personalizadas das colunas de saída da transformação Conversão de Dados. Todas as propriedades são de leitura/gravação.  
  
|Propriedade|Tipo de dados|DESCRIÇÃO|  
|--------------|---------------|-----------------|  
|FastParse|Boolean|Um valor que indica se as colunas usam as rotinas de análise mais rápidas, mas que não fazem distinção entre localidades, que o [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] fornece ou as rotinas de análise padrão que fazem distinção entre localidades. O valor padrão dessa propriedade é `False`. Para obter mais informações, consulte [Fast Parse](../../fast-parse.md) e [Standard Parse](../../standard-parse.md). .<br /><br /> Observação: Esta propriedade não está disponível no **Editor de Transformação da Conversão de Dados**, mas pode ser definida usando o **Editor Avançado**.|  
|SourceInputColumnLineageId|Integer|O `LineageID` da coluna de entrada que é fonte da coluna de saída.|  
  
 A entrada, as colunas de entrada e a saída da transformação Conversão de Dados não têm nenhuma propriedade personalizada.  
  
 Para obter mais informações, consulte [Data Conversion Transformation](data-conversion-transformation.md).  
  
##  <a name="dmquery"></a>Propriedades personalizadas da transformação consulta de mineração de dados  
 A transformação Consulta de Mineração de Dados tem as propriedades personalizadas e as propriedades comuns a todos os componentes de fluxo de dados.  
  
 A tabela a seguir descreve as propriedades personalizadas da transformação Consulta de Mineração de Dados. Todas as propriedades são de leitura/gravação.  
  
|Propriedade|Tipo de dados|DESCRIÇÃO|  
|--------------|---------------|-----------------|  
|ASConnectionId|String|O identificador exclusivo do objeto de conexão.|  
|ASConnectionString|String|A cadeia de conexão com um projeto do [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ou com um banco de dados do [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .|  
|CatalogName|String|O nome de um banco de dados do [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .|  
|ModelName|String|O nome do modelo de mineração de dados.|  
|ModelStructureName|String|O nome da estrutura de mineração.|  
|ObjectRef|String|Uma marca XML que identifica a estrutura de mineração de dados usada pela transformação.|  
|QueryText|String|A instrução de consulta de previsão usada pela transformação.|  
  
 A entrada, as colunas de entrada, a saída e as colunas de saída da transformação Consulta de Mineração de Dados não têm nenhuma propriedade personalizada.  
  
 Para obter mais informações, consulte [Data Mining Query Transformation](data-mining-query-transformation.md).  
  
##  <a name="derived"></a>Propriedades personalizadas da transformação coluna derivada  
 A transformação Coluna Derivada só tem as propriedades comuns a todos os componentes de fluxo de dados no nível do componente.  
  
 A tabela a seguir descreve as propriedades personalizadas das colunas de entrada e das colunas de saída da transformação Coluna Derivada. Quando você opta por adicionar a coluna derivada como uma coluna nova, essas propriedades personalizadas se aplicam à nova coluna de saída; quando você opta por substituir o conteúdo de uma coluna de entrada existente com os resultados derivados, essas propriedades personalizadas se aplicam à coluna de entrada existente. Todas as propriedades são de leitura/gravação.  
  
|Propriedade|Tipo de dados|DESCRIÇÃO|  
|--------------|---------------|-----------------|  
|Expression|String|Uma expressão que representa a condição avaliada pela transformação Divisão Condicional. Colunas são representadas pela propriedade `LineageID` da coluna.|  
|FriendlyExpression|String|Uma expressão que representa a condição avaliada pela transformação Divisão Condicional. Colunas são representadas pelos nomes.<br /><br /> O valor dessa propriedade pode ser especificado com uma expressão de propriedades.|  
  
 A entrada e a saída da transformação Coluna Derivada não têm nenhuma propriedade personalizada.  
  
 Para obter mais informações, consulte [Derived Column Transformation](derived-column-transformation.md).  
  
##  <a name="extract"></a>Propriedades personalizadas da transformação exportar coluna  
 A transformação Exportar Coluna só tem as propriedades comuns a todos os componentes de fluxo de dados no nível do componente.  
  
 A tabela a seguir descreve as propriedades personalizadas das colunas de entrada da transformação Exportar Coluna. Todas as propriedades são de leitura/gravação.  
  
|Propriedade|Tipo de dados|DESCRIÇÃO|  
|--------------|---------------|-----------------|  
|AllowAppend|Boolean|Um valor que especifica se a transformação acrescenta dados a um arquivo existente. O valor padrão dessa propriedade é `False`.|  
|ForceTruncate|Boolean|Um valor que especifica se a transformação trunca arquivos existentes antes de gravar dados. O valor padrão dessa propriedade é `False`.|  
|FileDataColumnID|Integer|Um valor que identifica a coluna que contém os dados inseridos pela transformação em um arquivo. Na coluna extrair, essa propriedade tem um valor de **0**; na coluna caminho do arquivo, essa propriedade contém o `LineageID` da coluna extrair.|  
|WriteBOM|Boolean|Um valor que especifica se uma marca de ordem de byte (BOM) é gravada no arquivo.|  
  
 A entrada, a saída e as colunas de saída da transformação Exportar Coluna não têm nenhuma propriedade personalizada.  
  
 Para obter mais informações, consulte [Export Column Transformation](export-column-transformation.md).  
  
##  <a name="insert"></a>Propriedades personalizadas da transformação importar coluna  
 A transformação Importar Coluna só tem as propriedades comuns a todos os componentes de fluxo de dados no nível do componente.  
  
 A tabela a seguir descreve as propriedades personalizadas das colunas de entrada da transformação Importar Coluna. Todas as propriedades são de leitura/gravação.  
  
|Propriedade|Tipo de dados|DESCRIÇÃO|  
|--------------|---------------|-----------------|  
|ExpectBOM|Boolean|Um valor que especifica se a transformação Importar Coluna deve esperar por uma marca de ordem de byte (BOM). Uma BOM só será esperada se os dados tiverem o tipo de dados de DT_NTEXT.|  
|FileDataColumnID|Integer|Um valor que identifica a coluna que contém os dados inseridos pela transformação no fluxo de dados. Na coluna de dados a ser inserida, essa propriedade tem um valor de 0; na coluna que contém os caminhos de arquivo de origem, essa propriedade contém o `LineageID` da coluna de dados a ser inserida.|  
  
 A entrada, a saída e as colunas de saída da transformação Importar Coluna não têm nenhuma propriedade personalizada.  
  
 Para obter mais informações, consulte [Import Column Transformation](import-column-transformation.md).  
  
##  <a name="fgroup"></a>Propriedades personalizadas da transformação Agrupamento Difuso  
 A transformação Agrupamento Difuso tem as propriedades personalizadas e as propriedades comuns a todos os componentes de fluxo de dados.  
  
 A tabela a seguir descreve as propriedades personalizadas da transformação Agrupamento Difuso. Todas as propriedades são de leitura/gravação.  
  
|Propriedade|Tipo de dados|DESCRIÇÃO|  
|--------------|---------------|-----------------|  
|Delimitadores|String|Os delimitadores de token usados pela transformação. Os delimitadores padrão incluem os seguintes caracteres: espaço ( ), vírgula (,), ponto final (.), ponto-e-vírgula (;), dois-pontos (:), hífen (-), aspas ("), apóstrofo ('), E comercial (&), barra (/), barra invertida (\\), arroba (@), ponto de exclamação (!), ponto de interrogação (?), parêntese de abertura ((), parêntese de fechamento ()), menor que (\<), maior que (>), colchete de abertura ([), colchete de fechamento (]), chave de abertura ({), chave de fechamento (}), barra vertical ou pipe (&#124;), número (#), asterisco (*), circunflexo (^) e porcentagem (%).|  
|Exhaustive|Boolean|Um valor que especifica se cada registro de entrada é comparado a todos os outros registros de entrada. O valor de `True` destina-se especialmente a propósitos de depuração. O valor padrão dessa propriedade é `False`.<br /><br /> Observação: Esta propriedade não está disponível no **Editor de Transformação do Agrupamento Difuso**, mas pode ser definida usando o **Editor Avançado**.|  
|MaxMemoryUsage|Integer|A quantidade máxima de memória para uso pela transformação. O valor padrão dessa propriedade é **0**, que ativa o uso de memória dinâmica.<br /><br /> O valor dessa propriedade pode ser especificado com uma expressão de propriedades.<br /><br /> Observação: Esta propriedade não está disponível no **Editor de Transformação do Agrupamento Difuso**, mas pode ser definida usando o **Editor Avançado**.|  
|MinSimilarity|DOUBLE|O limite de semelhança usado pela transformação para identificar duplicatas, expresso como um valor entre 0 e 1.  O valor padrão dessa propriedade é 0.8.|  
  
 A tabela a seguir descreve as propriedades personalizadas das colunas de entrada da transformação Agrupamento Difuso. Todas as propriedades são de leitura/gravação.  
  
|Propriedade|Tipo de dados|DESCRIÇÃO|  
|--------------|---------------|-----------------|  
|ExactFuzzy|Inteiro (enumeração)|Um valor que especifica se a transformação executa uma correspondência difusa ou uma correspondência exata. Os valores válidos são **Exato** e **Difuso**. O valor padrão para esta propriedade é **Difuso**.|  
|FuzzyComparisonFlags|Inteiro (enumeração)|Um valor que especifica como a transformação compara os dados de cadeia de caracteres em uma coluna. Essa propriedade pode ter um dos seguintes valores:<br /><br /> **FullySensitive**<br /><br /> **IgnoreCase**<br /><br /> **IgnoreKanaType**<br /><br /> **IgnoreNonSpace**<br /><br /> **IgnoreSymbols**<br /><br /> **IgnoreWidth**<br /><br /> <br /><br /> Para obter mais informações, consulte [Comparing String Data](../comparing-string-data.md).|  
|LeadingTrailingNumeralsSignificant|Inteiro (enumeração)|Um valor que especifica o significado de numerais. Essa propriedade pode ter um dos seguintes valores:<br /><br /> **LeadingNumeralsSignificant** (1) – use se os números à esquerda forem significativos.<br /><br /> **TrailingNumeralsSignificant** (2) – use se os numerais à direita forem significativos.<br /><br /> **LeadingAndTrailingNumeralsSignificant** (3) – use se os numerais à esquerda e à direita forem significativos.<br /><br /> **NumeralsNotSpecial** (0)-use se os numerais não forem significativos.|  
|MinSimilarity|DOUBLE|O limite de similaridade usado para a junção na coluna, especificado como um valor entre 0 e 1. Somente linhas superiores ao limite são classificadas como correspondências.|  
|ToBeCleaned|Boolean|Um valor que especifica se a coluna é usada para identificar duplicatas; ou seja, se é uma coluna na qual está ocorrendo agrupamento. O valor padrão dessa propriedade é `False`.|  
  
 A tabela a seguir descreve as propriedades personalizadas das colunas de saída da transformação Agrupamento Difuso. Todas as propriedades são de leitura/gravação.  
  
|Nome da propriedade|Tipo de dados|DESCRIÇÃO|  
|-------------------|---------------|-----------------|  
|ColumnType|Inteiro (enumeração)|Um valor que identifica o tipo de coluna de saída. Essa propriedade pode ter um dos seguintes valores:<br /><br /> **KeyIn** (1)<br /><br /> **KeyOut** (2)<br /><br /> **Similaridade** (3)<br /><br /> **ColumnSimilarity** (4)<br /><br /> **PassThru** (5)<br /><br /> **Canonica**l (6)<br /><br /> **Indefinido** (0)|  
|InputID|Integer|O `LineageID` da coluna de entrada correspondente.|  
  
 A entrada e a saída da transformação Agrupamento Difuso não têm nenhuma propriedade personalizada.  
  
 Para obter mais informações, consulte [Fuzzy Grouping Transformation](fuzzy-grouping-transformation.md).  
  
##  <a name="flookup"></a>Propriedades personalizadas da transformação pesquisa difusa  
 A transformação Pesquisa Difusa tem as propriedades personalizadas e as propriedades comuns a todos os componentes de fluxo de dados.  
  
 A tabela a seguir descreve as propriedades personalizadas da transformação Pesquisa Difusa. Todas as propriedades, exceto `ReferenceMetadataXML`, são de leitura/gravação.  
  
|Propriedade|Tipo de dados|DESCRIÇÃO|  
|--------------|---------------|-----------------|  
|CopyReferenceTable|Boolean|Especifica se uma cópia da tabela de referência deve ser feita para a criação do índice de pesquisa difusa e pesquisas subsequentes. O valor padrão dessa propriedade é `True`.|  
|Delimitadores|String|Os delimitadores usados pela transformação para criar tokens de valores de coluna. Os delimitadores padrão incluem os seguintes caracteres: espaço ( ), vírgula (,), ponto final (.), ponto e vírgula (;), dois pontos (:), hífen (-), aspas ("), apóstrofo ('), E comercial (&), barra (/), barra invertida (\\), arroba (@), ponto de exclamação (!), ponto de interrogação (?), parêntese de abertura ((), parêntese de fechamento ()), menor que (\<), maior que (>), colchete de abertura ([), colchete de fechamento (]), chave de abertura ({), chave de fechamento (}), pipe (&#124;). sinal de número (#), asterisco (*), acento circunflexo (^) e porcentagem (%).|  
|DropExistingMatchIndex|Boolean|Um valor que especifica se o índice de correspondência especificado em MatchIndexName é excluído quando MatchIndexOptions não é definido como ReuseExistingIndex. O valor padrão para essa propriedade é `True`.|  
|Exhaustive|Boolean|Um valor que especifica se cada registro de entrada é comparado a todos os outros registros de entrada. O valor de `True` destina-se especialmente a propósitos de depuração. O valor padrão dessa propriedade é `False`.<br /><br /> Observação: Esta propriedade não está disponível no **Editor de Transformação da Pesquisa Difusa**, mas pode ser definida usando o **Editor Avançado**.|  
|MatchIndexName|String|O nome do índice de correspondência. O índice de correspondência é a tabela na qual a transformação cria e salva o índice usado. Se o índice de correspondência for reutilizado, MatchIndexName especificará o índice a ser reutilizado. MatchIndexName deve ser um nome de identificador válido do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Por exemplo, se o nome contiver espaços, deverá ser colocado entre colchetes.|  
|MatchIndexOptions|Inteiro (enumeração)|Um valor que especifica como a transformação gerencia o índice de correspondência. Essa propriedade pode ter um dos seguintes valores:<br /><br /> `ReuseExistingIndex`0<br /><br /> **GenerateNewIndex** (1)<br /><br /> **GenerateAndPersistNewIndex** (2)<br /><br /> **GenerateAndMaintainNewIndex** (3)|  
|MaxMemoryUsage|Integer|O tamanho máximo do cache para a tabela de pesquisa. O valor padrão desta propriedade é **0**, o que significa que não há limite para o tamanho do cache.<br /><br /> O valor dessa propriedade pode ser especificado com uma expressão de propriedades.<br /><br /> Observação: Esta propriedade não está disponível no **Editor de Transformação da Pesquisa Difusa**, mas pode ser definida usando o **Editor Avançado**.|  
|MaxOutputMatchesPerInput|Integer|O número máximo de correspondências que a transformação pode retornar para cada linha de entrada. O valor padrão dessa propriedade é **1**.<br /><br /> Observação: Valores superiores a 100 só podem ser especificados usando o **Editor Avançado**.|  
|MinSimilarity|Integer|O limite de similaridade usado pela transformação no nível do componente, especificado como um valor entre 0 e 1. Somente linhas superiores ao limite são classificadas como correspondências.|  
|ReferenceMetadataXML|String|[!INCLUDE[ssInternalOnly](../../../includes/ssinternalonly-md.md)]|  
|ReferenceTableName|String|O nome da tabela de pesquisa. O nome deve ser um nome de identificador válido do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Por exemplo, se o nome contiver espaços, deverá ser colocado entre colchetes.|  
|WarmCaches|Boolean|Quando verdadeiro, a pesquisa carrega o índice e a tabela de referência parcialmente na memória antes do início da execução. Isso pode melhorar o desempenho.|  
  
 A tabela a seguir descreve as propriedades personalizadas das colunas de entrada da transformação Pesquisa Difusa. Todas as propriedades são de leitura/gravação.  
  
|Propriedade|Tipo de dados|DESCRIÇÃO|  
|--------------|---------------|-----------------|  
|FuzzyComparisonFlags|Integer|Um valor que especifica como a transformação compara os dados de cadeia de caracteres em uma coluna. Para obter mais informações, consulte [Comparing String Data](../comparing-string-data.md).|  
|FuzzyComparisonFlagsEx|Inteiro (enumeração)|Um valor que especifica quais sinalizadores de comparação estendida são usados pela transformação. Os valores podem incluir **MapExpandLigatures, MapFoldCZone**, **MapFoldDigits**, **MapPrecomposed**e **NoMapping**. **NoMapping** não pode ser usado com outros sinalizadores.|  
|JoinToReferenceColumn|String|Um valor que especifica o nome da coluna na tabela de referência à qual a coluna é unida.|  
|JoinType|Integer|Um valor que especifica se a transformação executa uma correspondência difusa ou uma correspondência exata. O valor padrão para esta propriedade é **Difuso**. O valor inteiro para o tipo de junção exata é **1** e o valor do tipo de junção difusa é **2**.|  
|MinSimilarity|DOUBLE|O limite de similaridade usado pela transformação no nível da coluna, especificado como um valor entre 0 e 1. Somente linhas superiores ao limite são classificadas como correspondências.|  
  
 A tabela a seguir descreve as propriedades personalizadas das colunas de saída da transformação Pesquisa Difusa. Todas as propriedades são de leitura/gravação.  
  
> [!NOTE]  
>  Para colunas de saída que contêm valores de passagem das colunas de entrada correspondentes, CopyFromReferenceColumn está vazio e SourceInputColumnLineageID `LineageID` contém a da coluna de entrada correspondente. Em colunas de saída que contêm resultados de pesquisa, CopyFromReferenceColumn contém o nome da coluna de pesquisa e SourceInputColumnLineageID fica vazio.  
  
|Propriedade|Tipo de dados|DESCRIÇÃO|  
|--------------|---------------|-----------------|  
|ColumnType|Inteiro (enumeração)|Um valor que identifica o tipo de coluna de saída para colunas que a transformação adiciona à saída. Essa propriedade pode ter um dos seguintes valores:<br /><br /> **Similaridade** (1)<br /><br /> **Confiança** (2)<br /><br /> **ColumnSimilarity** (3)<br /><br /> **Indefinido** (0)|  
|CopyFromReferenceColumn|String|Um valor que especifica o nome da coluna na tabela de referência que fornece o valor em uma coluna de saída.|  
|SourceInputColumnLineageId|Integer|Um valor que identifica a coluna de entrada que fornece valores a esta coluna de saída.|  
  
 A entrada e a saída da transformação Pesquisa Difusa não têm nenhuma propriedade personalizada.  
  
 Para obter mais informações, consulte [Fuzzy Lookup Transformation](lookup-transformation.md).  
  
##  <a name="lookup"></a>Propriedades personalizadas da transformação pesquisa  
 A transformação Pesquisa tem as propriedades personalizadas e as propriedades comuns a todos os componentes de fluxo de dados.  
  
 A tabela a seguir descreve as propriedades personalizadas da transformação Pesquisa. Todas as propriedades, exceto `ReferenceMetadataXML`, são de leitura/gravação.  
  
|Propriedade|Tipo de dados|DESCRIÇÃO|  
|--------------|---------------|-----------------|  
|CacheType|Inteiro (enumeração)|O tipo de cache da tabela de pesquisa. Os valores são **Cheio** (0), **Parcial** (1) e **Nenhum** (2). O valor padrão dessa propriedade é **Cheio**.|  
|DefaultCodePage|Integer|A página de código padrão a ser usada quando informações de página de código não estão disponíveis na fonte de dados.|  
|MaxMemoryUsage|Integer|O tamanho máximo do cache para a tabela de pesquisa. O valor padrão desta propriedade é **25**, o que significa que não há limite para o tamanho do cache.|  
|MaxMemoryUsage64|Integer|O tamanho máximo do cache para a tabela de pesquisa em um computador de 64 bits.|  
|NoMatchBehavior|Inteiro (enumeração)|Um valor que especifica se linhas sem entradas de correspondência no conjunto de dados de referência são tratadas como erros.<br /><br /> Quando a propriedade é definida como `Treat rows with no matching entries as errors` (0), as linhas sem entradas correspondentes são tratadas como erros. É possível especificar o que deve acontecer quando esse tipo de erro ocorre usando a página **Saída de Erro** da caixa de diálogo **Editor de Transformação Pesquisa** . Para obter mais informações, consulte [Editor de Transformação Pesquisa &#40;página Saída de Erro&#41;](../../lookup-transformation-editor-error-output-page.md).<br /><br /> Quando a propriedade é definida como `Send rows with no matching entries to the no match output` (1), as linhas não são tratadas como erros.<br /><br /> O valor padrão é `Treat rows with no matching entries as errors` (0).|  
|ParameterMap|String|Uma lista delimitada por ponto-e-vírgula de IDs de linhagem que são mapeadas para os parâmetros usados na instrução `SqlCommand`.|  
|ReferenceMetadataXML|String|Metadados para as colunas na tabela de pesquisa copiados pela transformação para a sua saída.|  
|SqlCommand|String|A instrução SELECT que popula a tabela de pesquisa.|  
|SqlCommandParam|String|A instrução SQL com parâmetros que popula a tabela de pesquisa.|  
  
 A tabela a seguir descreve as propriedades personalizadas das colunas de entrada da transformação Pesquisa. Todas as propriedades são de leitura/gravação.  
  
|Propriedade|Tipo de dados|DESCRIÇÃO|  
|--------------|---------------|-----------------|  
|CopyFromReferenceColumn|String|O nome da coluna na tabela de referência da qual uma coluna é copiada.|  
|JoinToReferenceColumns|String|O nome da coluna na tabela de referência à qual uma de coluna de origem é unida.|  
  
 A tabela a seguir descreve as propriedades personalizadas das colunas de saída da transformação Pesquisa. Todas as propriedades são de leitura/gravação.  
  
|Nome da propriedade|Tipo de dados|DESCRIÇÃO|  
|-------------------|---------------|-----------------|  
|CopyFromReferenceColumn|String|O nome da coluna na tabela de referência da qual uma coluna é copiada.|  
  
 A entrada e a saída da transformação Pesquisa não têm nenhuma propriedade personalizada.  
  
 Para obter mais informações, consulte [Lookup Transformation](lookup-transformation.md).  
  
##  <a name="mjoin"></a>Propriedades personalizadas da transformação junção de mesclagem  
 A transformação Mesclar Junção tem as propriedades personalizadas e as propriedades comuns a todos os componentes de fluxo de dados.  
  
 A tabela a seguir descreve as propriedades personalizadas da transformação Mesclar Junção.  
  
|Propriedade|Tipo de dados|DESCRIÇÃO|  
|--------------|---------------|-----------------|  
|JoinType|Inteiro (enumeração)|Especifica se a junção é uma junção interna (2), esquerda externa (1) ou cheia (0).|  
|MaxBuffersPerInput|Integer|Não é mais preciso configurar o valor da propriedade `MaxBuffersPerInput`, pois a Microsoft fez alterações que reduzem o risco de a transformação Junção de Mesclagem consumir memória excessiva. Esse problema algumas vezes ocorria quando as várias entradas da Junção de Mesclagem geravam dados a taxas irregulares.|  
|NumKeyColumns|Integer|O número de colunas usadas na junção.|  
|TreatNullsAsEqual|Boolean|Um valor que especifica se a transformação controla valores nulos como valores iguais. O valor padrão dessa propriedade é `True`. Se o valor de propriedade for `False`, a transformação controlará valores nulos, como faz o [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
  
 A tabela a seguir descreve as propriedades personalizadas das colunas de saída da transformação Mesclar Junção. Todas as propriedades são de leitura/gravação.  
  
|Nome da propriedade|Tipo de dados|DESCRIÇÃO|  
|-------------------|---------------|-----------------|  
|InputColumnID|Integer|O `LineageID` da coluna de entrada da qual são copiados dados para esta coluna de saída.|  
  
 A entrada, as colunas de entrada e a saída da transformação Mesclar Junção não têm nenhuma propriedade personalizada.  
  
 Para obter mais informações, consulte [Merge Join Transformation](merge-join-transformation.md).  
  
##  <a name="oledbcmd"></a>Propriedades personalizadas da transformação comando OLE DB  
 A transformação Comando OLE DB tem as propriedades personalizadas e as propriedades comuns a todos os componentes de fluxo de dados.  
  
 A tabela a seguir descreve as propriedades personalizadas da transformação Comando OLE DB.  
  
|Nome da propriedade|Tipo de dados|DESCRIÇÃO|  
|-------------------|---------------|-----------------|  
|CommandTimeOut|Integer|O número máximo de segundos que o comando SQL pode executar antes de atingir o tempo limite. Um valor de **0** indica um tempo infinito. O valor padrão dessa propriedade é **0**.|  
|DefaultCodePage|Integer|A página de código a ser usada quando informações de página de código não estão disponíveis na fonte de dados.|  
|SqlCommand|String|A instrução Transact-SQL executada pela transformação para cada linha no fluxo de dados.<br /><br /> O valor dessa propriedade pode ser especificado com uma expressão de propriedades.|  
  
 A tabela seguinte descreve as propriedades personalizadas das colunas externas da transformação Comando OLE DB. Todas as propriedades são de leitura/gravação.  
  
|Nome da propriedade|Tipo de dados|DESCRIÇÃO|  
|-------------------|---------------|-----------------|  
|DBParamInfoFlag|Integer (bitmask)|Um conjunto de sinalizadores que descrevem características de parâmetro. Para obter mais informações, consulte o DBPARAMFLAGSENUM na documentação de OLE DB na Biblioteca MSDN.|  
  
 A entrada, as colunas de entrada, a saída e as colunas de saída da transformação Comando OLE DB não têm nenhuma propriedade personalizada.  
  
 Para obter mais informações, consulte [OLE DB Command Transformation](ole-db-command-transformation.md).  
  
##  <a name="percent"></a>Propriedades personalizadas da transformação amostragem percentual  
 A transformação Amostragem Percentual tem as propriedades personalizadas e as propriedades comuns a todos os componentes de fluxo de dados.  
  
 A tabela a seguir descreve as propriedades personalizadas da transformação Amostragem Percentual.  
  
|Propriedade|Tipo de dados|DESCRIÇÃO|  
|--------------|---------------|-----------------|  
|SamplingSeed|Integer|A semente usada pelo gerador aleatório de números. O valor padrão desta propriedade é **0**, indicando que a transformação usa uma contagem de tiques.|  
|SamplingValue|Integer|O tamanho da amostra como uma porcentagem da fonte.<br /><br /> O valor dessa propriedade pode ser especificado com uma expressão de propriedades.|  
  
 A tabela a seguir descreve as propriedades personalizadas das saídas da transformação Amostragem Percentual. Todas as propriedades são de leitura/gravação.  
  
|Nome da propriedade|Tipo de dados|DESCRIÇÃO|  
|-------------------|---------------|-----------------|  
|Selecionado|Boolean|Designa a saída para a qual as linhas de amostra são direcionadas. Na saída selecionada, selecionado é definido como `True`e, na saída não selecionada, selecionado é definido como. `False`|  
  
 A entrada, as colunas de entrada e as colunas de saída da transformação Amostragem Percentual não têm nenhuma propriedade personalizada.  
  
 Para obter mais informações, consulte [Percentage Sampling Transformation](percentage-sampling-transformation.md).  
  
##  <a name="pivot"></a>Propriedades personalizadas da transformação dinâmica  
 A tabela a seguir descreve as propriedades personalizadas dos componentes da transformação Dinâmica.  
  
|Propriedade|Tipo de dados|DESCRIÇÃO|  
|--------------|---------------|-----------------|  
|**PassThroughUnmatchedPivotKeyts**|Boolean|Defina como `True` para configurar a transformação Dinâmica para ignorar as linhas que contêm valores não reconhecidos na coluna Chave Dinâmica e gerar todos os valores de chave dinâmica para uma mensagem de log, quando o pacote é executado.|  
  
 A tabela a seguir descreve as propriedades personalizadas das colunas de entrada da transformação Dinâmica. Todas as propriedades são de leitura/gravação.  
  
|Propriedade|Tipo de dados|DESCRIÇÃO|  
|--------------|---------------|-----------------|  
|PivotUsage|Inteiro (enumeração)|Um dos seguintes valores que especificam a função de uma coluna quando o conjunto de dados é dinamizado:<br /><br /> **0**: a coluna não é dinamizada e os valores da coluna são passados para a saída da transformação.<br /><br /> **1**: a coluna faz parte da chave definida que identifica uma ou mais linhas como parte de um conjunto. Todas as linhas de entrada com a mesma chave definida são combinadas em uma linha de saída.<br /><br /> **2**: a coluna é uma coluna dinâmica. Pelo menos uma coluna é criada a partir de cada valor da coluna.<br /><br /> **3**: os valores dessa coluna são colocados em colunas que são criadas como resultado da tabela dinâmica.|  
  
 A tabela a seguir descreve as propriedades personalizadas das colunas de saída da transformação Dinâmica. Todas as propriedades são de leitura/gravação.  
  
|Propriedade|Tipo de dados|DESCRIÇÃO|  
|--------------|---------------|-----------------|  
|PivotKeyValue|String|Um dos possíveis valores da coluna assinalada como a chave dinâmica pelo valor de sua propriedade PivotUsage.<br /><br /> O valor dessa propriedade pode ser especificado com uma expressão de propriedades.|  
|SourceColumn|Integer|O `LineageID` de uma coluna de entrada que contém um valor dinâmico ou -1. O valor de -1 indica que a coluna não é usada em uma operação dinâmica.|  
  
 Para obter mais informações, consulte [Pivot Transformation](pivot-transformation.md).  
  
##  <a name="rowcount"></a>Propriedades personalizadas da transformação contagem de linhas  
 A transformação Contagem de Linhas tem as propriedades personalizadas e as propriedades comuns a todos os componentes de fluxo de dados.  
  
 A tabela a seguir descreve as propriedades personalizadas da transformação Contagem de Linhas. Todas as propriedades são de leitura/gravação.  
  
|Nome da propriedade|Tipo de dados|DESCRIÇÃO|  
|-------------------|---------------|-----------------|  
|VariableName|String|O nome da variável que contém a contagem de linhas.|  
  
 A entrada, as colunas de entrada, a saída e as colunas de saída da transformação Contagem de Linhas não têm nenhuma propriedade personalizada.  
  
 Para obter mais informações, consulte [Row Count Transformation](row-count-transformation.md).  
  
##  <a name="rowsamp"></a>Propriedades personalizadas da transformação amostragem de linhas  
 A transformação Amostragem de Linhas tem as propriedades personalizadas e as propriedades comuns a todos os componentes de fluxo de dados.  
  
 A tabela a seguir descreve as propriedades personalizadas da transformação Amostragem de Linhas. Todas as propriedades são de leitura/gravação.  
  
|Propriedade|Tipo de dados|DESCRIÇÃO|  
|--------------|---------------|-----------------|  
|SamplingSeed|Integer|A semente usada pelo gerador aleatório de números. O valor padrão desta propriedade é **0**, indicando que a transformação usa uma contagem de tiques.|  
|SamplingValue|Integer|A contagem de linhas da amostra.<br /><br /> O valor dessa propriedade pode ser especificado com uma expressão de propriedades.|  
  
 A tabela a seguir descreve as propriedades personalizadas das saídas da transformação Amostragem de Linhas. Todas as propriedades são de leitura/gravação.  
  
|Nome da propriedade|Tipo de dados|DESCRIÇÃO|  
|-------------------|---------------|-----------------|  
|Selecionado|Boolean|Designa a saída para a qual as linhas de amostra são direcionadas. Na saída selecionada, selecionado é definido como `True`e, na saída não selecionada, selecionado é definido como. `False`|  
  
 A tabela a seguir descreve as propriedades personalizadas das colunas de saída da transformação Amostragem de Linhas. Todas as propriedades são de leitura/gravação.  
  
|Propriedade|Tipo de dados|DESCRIÇÃO|  
|--------------|---------------|-----------------|  
|InputColumnLineageId|Integer|Um valor que especifica o `LineageID` da coluna de entrada que é a fonte da coluna de saída.|  
  
 A entrada e as colunas de entrada da transformação Amostragem de Linhas não têm nenhuma propriedade personalizada.  
  
 Para obter mais informações, consulte [Row Sampling Transformation](row-sampling-transformation.md).  
  
##  <a name="script"></a>Propriedades personalizadas do componente de script  
 O Componente de Script tem propriedades personalizadas e as propriedades comum a todos os componentes de fluxo de dados. As mesmas propriedades personalizadas ficarão disponíveis se o Componente de Script funcionar como uma fonte, transformação ou destino.  
  
 A tabela a seguir descreve as propriedades personalizadas do Componente de Script. Todas as propriedades são de leitura/gravação.  
  
|Nome da propriedade|Tipo de dados|DESCRIÇÃO|  
|-------------------|---------------|-----------------|  
|ReadOnlyVariables|String|Uma lista de variáveis separadas por vírgulas disponível para o Componente de Script para acesso em modo somente leitura.|  
|ReadWriteVariables|String|Uma lista de variáveis separadas por vírgulas disponível para o Componente de Script para acesso em modo leitura/gravação.|  
  
 A entrada, as colunas de entrada, a saída e as colunas de saída do Componente de Script não têm propriedades personalizadas, a menos que sejam criadas pelo desenvolvedor de scripts.  
  
 Para obter mais informações, consulte [Script Component](script-component.md).  
  
##  <a name="scd"></a>Propriedades personalizadas da transformação Dimensão de alteração lenta  
 A transformação Dimensão de Alteração Lenta tem propriedades personalizadas e as propriedades comum a todos os componentes de fluxo de dados.  
  
 A tabela a seguir descreve as propriedades personalizadas da transformação Dimensão de Alteração Lenta. Todas as propriedades são de leitura/gravação.  
  
|Propriedade|Tipo de dados|DESCRIÇÃO|  
|--------------|---------------|-----------------|  
|CurrentRowWhere|String|A cláusula WHERE na instrução SELECT que seleciona a linha atual entre linhas com a mesma chave de negócio.|  
|EnableInferredMember|Boolean|Um valor que especifica se atualizações de membros inferidos foram detectadas. O valor padrão dessa propriedade é `True`.|  
|FailOnFixedAttributeChange|Boolean|Um valor que especifica se a transformação falha quando colunas de linha com atributos fixos contêm alterações ou a pesquisa na tabela da dimensão falha. Se você espera que linhas de entrada contenham novos registros, defina este valor como `True` para que a transformação continue após a falha na pesquisa, já que ela usa a falha para identificar novos registros. O valor padrão dessa propriedade é `False`.|  
|FailOnLookupFailure|Boolean|Um valor que especifica se a transformação falha quando a pesquisa de um registro existente falha. O valor padrão dessa propriedade é `False`.|  
|IncomingRowChangeType|Integer|Um valor que especifica se todas as linhas de entrada são novas ou se a transformação deve detectar o tipo de alteração.|  
|InferredMemberIndicator|String|O nome de coluna para o membro inferido.|  
|SqlCommand|String|A instrução SQL usada para criar um conjunto de linhas de esquema.|  
|UpdateChangingAttributeHistory|Boolean|Um valor que indica se atualizações de atributo de histórico são direcionadas à saída da transformação para alteração de atualizações de atributos.|  
  
 A tabela a seguir descreve as propriedades personalizadas das colunas de entrada da transformação Dimensão de Alteração Lenta. Todas as propriedades são de leitura/gravação.  
  
|Propriedade|Tipo de dados|DESCRIÇÃO|  
|--------------|---------------|-----------------|  
|ColumnType|Inteiro (enumeração)|O tipo de atualização da coluna. Os valores são: **Atributo de Alteração** (2), **Atributo Fixo** (4), **Atributo Histórico** (3), **Chave** (1) e **Outro** (0).|  
  
 A entrada, as saídas e as colunas de saída da transformação Dimensão de Alteração Lenta não têm nenhuma propriedade personalizada.  
  
 Para obter mais informações, consulte [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md).  
  
##  <a name="sort"></a>Propriedades personalizadas da transformação Classificação  
 A transformação Classificar tem as propriedades personalizadas e as propriedades comuns a todos os componentes de fluxo de dados.  
  
 A tabela a seguir descreve as propriedades personalizadas da transformação Classificar. Todas as propriedades são de leitura/gravação.  
  
|Propriedade|Tipo de dados|DESCRIÇÃO|  
|--------------|---------------|-----------------|  
|EliminateDuplicates|Boolean|Especifica se a transformação remove linhas duplicadas da saída da transformação. O valor padrão dessa propriedade é `False`.|  
|MaximumThreads|Integer|Contém o número máximo de threads que a transformação pode usar para classificar. Um valor **0** indica que não há limite de threads. O valor padrão dessa propriedade é **0**.<br /><br /> O valor dessa propriedade pode ser especificado com uma expressão de propriedades.|  
  
 A tabela a seguir descreve as propriedades personalizadas das colunas de entrada da transformação Classificar. Todas as propriedades são de leitura/gravação.  
  
|Propriedade|Tipo de dados|DESCRIÇÃO|  
|--------------|---------------|-----------------|  
|NewComparisonFlags|Integer (bitmask)|Um valor que especifica como a transformação compara os dados de cadeia de caracteres em uma coluna. Para obter mais informações, consulte [Comparing String Data](../comparing-string-data.md).|  
|NewSortKeyPosition|Integer|Um valor que especifica a ordem de classificação da coluna. Um valor de 0 indica que os dados não são classificados nesta coluna.|  
  
 A tabela a seguir descreve as propriedades personalizadas das colunas de saída da transformação Classificar. Todas as propriedades são de leitura/gravação.  
  
|Propriedade|Tipo de dados|DESCRIÇÃO|  
|--------------|---------------|-----------------|  
|SortColumnID|Integer|O `LineageID` de uma coluna de classificação.|  
  
 A entrada e a saída da transformação Classificar não têm nenhuma propriedade personalizada.  
  
 Para obter mais informações, consulte [Sort Transformation](sort-transformation.md).  
  
##  <a name="textract"></a>Propriedades personalizadas da transformação Extração de termos  
 A transformação Extração de Termos tem as propriedades personalizadas e as propriedades comuns a todos os componentes de fluxo de dados.  
  
 A tabela a seguir descreve as propriedades personalizadas da transformação Extração de Termos. Todas as propriedades são de leitura/gravação.  
  
|Propriedade|Tipo de dados|DESCRIÇÃO|  
|--------------|--------------|-----------------|  
|FrequencyThreshold|Integer|Um valor numérico que indica o número de vezes que um termo deve ocorrer antes de ser extraído. O valor padrão dessa propriedade é **2**.|  
|IsCaseSensitive|Boolean|Um valor que especifica se a diferenciação de maiúsculas e minúsculas é usada na extração de substantivos e frases nominais. O valor padrão dessa propriedade é `False`.|  
|MaxLengthOfTerm|Integer|Um valor numérico que indica o comprimento máximo de um termo. Esta propriedade só se aplica a frases. O valor padrão dessa propriedade é **12**.|  
|NeedRefenceData|Boolean|Um valor que especifica se a transformação usa uma lista de termos de exclusão armazenada em uma tabela de referência. O valor padrão dessa propriedade é `False`.|  
|OutTermColumn|String|O nome da coluna que contém os termos de exclusão.|  
|OutTermTable|String|O nome da tabela que contém a coluna com termos de exclusão.|  
|ScoreType|Integer|Um valor que especifica o tipo de pontuação a ser associado ao termo. Os valores válidos são 0 (frequência) e 1 (pontuação TFIDF). A pontuação TFIDF é o produto da Frequência do Termo e da Frequência de Documento Inversa, definido como: TFIDF de um termo T = (frequência de T) \* log ((nºs de linhas na Entrada) / (nº de linhas com T)). O valor padrão dessa propriedade é **0**.|  
|WordOrPhrase|Integer|Um valor que especifica o tipo de termo. Os valores válidos são 0 (somente palavras), 1 (somente frases nominais) e 2 (palavras e frases nominais). O valor padrão dessa propriedade é **0**.|  
  
 A entrada, as colunas de entrada, a saída e as colunas de saída da transformação Contagem de Linhas não têm nenhuma propriedade personalizada.  
  
 Para obter mais informações, consulte [Term Extraction Transformation](term-extraction-transformation.md).  
  
##  <a name="tlookup"></a>Propriedades personalizadas da transformação pesquisa de termos  
 A transformação Pesquisa de Termos tem as propriedades personalizadas e as propriedades comuns a todos os componentes de fluxo de dados.  
  
 A tabela a seguir descreve as propriedades personalizadas da transformação Pesquisa de Termos. Todas as propriedades são de leitura/gravação.  
  
|Propriedade|Tipo de dados|DESCRIÇÃO|  
|--------------|---------------|-----------------|  
|IsCaseSensitive|Boolean|Um valor que especifica se uma comparação que faz distinção entre letras maiúsculas e minúsculas é aplicável à correspondência do texto da coluna de entrada e do termo da pesquisa. O valor padrão dessa propriedade é `False`.|  
|RefTermColumn|String|O nome da coluna que contém os termos da pesquisa.|  
|RefTermTable|String|O nome da tabela que contém a coluna com termos da pesquisa.|  
  
 A tabela a seguir descreve as propriedades personalizadas das colunas de entrada da transformação Pesquisa de Termos. Todas as propriedades são de leitura/gravação.  
  
|Propriedade|Tipo de dados|DESCRIÇÃO|  
|--------------|---------------|-----------------|  
|InputColumnType|Integer|Um valor que especifica o uso da coluna. Os valores válidos são 0 (coluna de passagem), 1 (coluna de pesquisa) e 2 (coluna de passagem e de pesquisa).|  
  
 A tabela a seguir descreve as propriedades personalizadas das colunas de saída da transformação Pesquisa de Termos. Todas as propriedades são de leitura/gravação.  
  
|Nome da propriedade|Tipo de dados|DESCRIÇÃO|  
|-------------------|---------------|-----------------|  
|CustomLineageID|Integer|O `LineageID` da coluna de entrada correspondente se o `InputColumnType` dela for 0 ou 2.|  
  
 A entrada e a saída da transformação Pesquisa de Termos não têm nenhuma propriedade personalizada.  
  
 Para obter mais informações, consulte [Term Lookup Transformation](term-lookup-transformation.md).  
  
##  <a name="unpivot"></a>Propriedades personalizadas da transformação não dinâmica  
 A transformação Não Dinâmica só tem as propriedades comuns a todos os componentes de fluxo de dados no nível do componente.  
  
> [!NOTE]  
>  Esta seção tem como base o cenário da transformação Não Dinâmica descrito em [Transformação Não Dinâmica](unpivot-transformation.md) para ilustrar o uso das opções descritas aqui.  
  
 A tabela a seguir descreve as propriedades personalizadas das colunas de entrada da transformação Não Dinâmica. Todas as propriedades são de leitura/gravação.  
  
|Propriedade|Tipo de dados|DESCRIÇÃO|  
|--------------|---------------|-----------------|  
|DestinationColumn|Integer|O `LineageID` da coluna de saída para a qual coluna de entrada é mapeada. Um valor de -1 indica que a coluna de entrada não é mapeada para uma coluna de saída.|  
|PivotKeyValue|String|Um valor que é copiado em uma coluna de saída de transformação.<br /><br /> O valor dessa propriedade pode ser especificado com uma expressão de propriedades.<br /><br /> No cenário da transformação Não Dinâmica descrito em [Unpivot Transformation](unpivot-transformation.md), os Valores Dinâmicos são os valores de texto Ham, Coke, Milk, Beer e Chips. Serão exibidos como valores de texto na nova coluna Produto designada pela opção **Nome da Coluna de Valores de Chaves Dinâmicas** .|  
  
 A tabela a seguir descreve as propriedades personalizadas das colunas de saída da transformação Não Dinâmica. Todas as propriedades são de leitura/gravação.  
  
|Nome da propriedade|Tipo de dados|DESCRIÇÃO|  
|-------------------|---------------|-----------------|  
|PivotKey|Boolean|Indica se os valores na propriedade `PivotKeyValue` de colunas de entrada são gravados nesta coluna de saída.<br /><br /> No cenário da transformação Não Dinâmica descrito em [Unpivot Transformation](unpivot-transformation.md), o nome da coluna de Valores Dinâmicos é **Produto** e designa a nova coluna **Produto** , na qual as colunas Ham, Coke, Milk, Beer e Chips não são dinâmicos.|  
  
 A entrada e a saída da transformação Não Dinâmica não têm nenhuma propriedade personalizada.  
  
 Para obter mais informações, consulte [Unpivot Transformation](unpivot-transformation.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Transformações do Integration Services](integration-services-transformations.md)   
 [Propriedades comuns](../../common-properties.md)   
 [Propriedades do caminho](../../path-properties.md)   
 [Propriedades de fluxo de dados que podem ser definidas usando expressões](../../data-flow-properties-that-can-be-set-by-using-expressions.md)  
  
  
