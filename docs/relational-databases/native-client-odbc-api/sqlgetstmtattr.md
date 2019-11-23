---
title: SQLGetStmtAttr | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLGetStmtAttr function
ms.assetid: e64f4f94-eb73-4477-9745-080b6cbdc751
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 198c3c8e5752aebc58726b2e7478632adf2c1bd0
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73786287"
---
# <a name="sqlgetstmtattr"></a>SQLGetStmtAttr
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  O driver ODBC do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client estende SQLGetStmtAttr para expor atributos de instrução específicos do driver.  
  
 [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) lista atributos de instrução que sejam de leitura e gravação. Este tópico lista os atributos de instrução somente leitura.  
  
## <a name="sql_sopt_ss_current_command"></a>SQL_SOPT_SS_CURRENT_COMMAND  
 O atributo SQL_SOPT_SS_CURRENT_COMMAND expõe o comando atual de um lote de comando. O retorno é um inteiro que especifica o local do comando no lote. O valor *ValuePtr* é do tipo SQLLEN.  
  
## <a name="sql_sopt_ss_nocount_status"></a>SQL_SOPT_SS_NOCOUNT_STATUS  
 O atributo SQL_SOPT_SS_NOCOUNT_STATUS indica a configuração atual da opção NOCOUNT, que controla se o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] relata o número de linhas afetadas por uma instrução quando [SQLRowCount](../../relational-databases/native-client-odbc-api/sqlrowcount.md) é chamado. O valor *ValuePtr* é do tipo SQLLEN.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SQL_NC_OFF|NOCOUNT é OFF. SQLRowCount retorna o número de linhas afetadas.|  
|SQL_NC_ON|NOCOUNT é ON. O número de linhas afetadas não é retornado por SQLRowCount e o valor retornado é 0.|  
  
 Se SQLRowCount retornar 0, o aplicativo deverá testar SQL_SOPT_SS_NOCOUNT_STATUS. Se SQL_NC_ON for retornado, o valor de 0 de SQLRowCount indicará apenas que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] não retornou uma contagem de linhas. Se SQL_NC_OFF for retornado, significa que NOCOUNT está desativado e o valor de 0 de SQLRowCount indica que a instrução não afetou nenhuma linha.  
  
 Os aplicativos não devem exibir o valor de SQLRowCount quando SQL_SOPT_SS_NOCOUNT_STATUS for SQL_NC_OFF. Lotes grandes ou procedimentos armazenados podem conter várias instruções SET NOCOUNT, portanto não é possível supor que SQL_SOPT_SS_NOCOUNT_STATUS permaneça constante. Essa opção deve ser testada cada vez que SQLRowCount retorna 0.  
  
## <a name="sql_sopt_ss_querynotification_msgtext"></a>SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT  
 O atributo SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT retorna o texto de mensagem para a solicitação de notificação de consulta.  
  
## <a name="sqlgetstmtattr-and-table-valued-parameters"></a>SQLGetStmtAttr e Parâmetros com valor de tabela  
 SQLGetStmtAttr pode ser chamado para obter o valor de SQL_SOPT_SS_PARAM_FOCUS no descritor de parâmetro do aplicativo (APD) ao trabalhar com parâmetros com valor de tabela. Para obter mais informações sobre SQL_SOPT_SS_PARAM_FOCUS, consulte [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).  
  
 Para obter mais informações sobre parâmetros com valor de tabela, consulte [parâmetros &#40;com valor&#41;de tabela ODBC](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>Consulte também  
 [Função SQLSetStmtAttr](https://go.microsoft.com/fwlink/?LinkId=59370)   
 [Detalhes da implementação da API do ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
