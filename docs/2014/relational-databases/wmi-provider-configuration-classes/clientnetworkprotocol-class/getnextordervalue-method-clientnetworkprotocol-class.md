---
title: Método GetNextOrderValue (classe ClientNetworkProtocol) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- GetNextOrderValue Method (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- GetNextOrderValue method
ms.assetid: d741dc5c-c225-43d9-a730-7ad664ac525f
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 8f5d7f8efe305be71a311b822c51ff1ede9afdf9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62691491"
---
# <a name="getnextordervalue-method-clientnetworkprotocol-class"></a>Método GetNextOrderValue (classe ClientNetworkProtocol)
  Seleciona o protocolo que está na próxima posição na lista de protocolos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
object  
.GetNextOrderValue()  
  
```  
  
## <a name="parts"></a>Partes  
 *objeto*  
 Um objeto da [classe ClientNetworkProtocol](clientnetworkprotocol-class.md) que representa o protocolo de rede usado [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pelo cliente.  
  
## <a name="property-valuereturn-value"></a>Valor da propriedade/Valor do retorno  
 Um valor `uint32`, que é 0 se o serviço tiver sido modificado com êxito, 1 se a solicitação não tiver suporte e qualquer outro número para indicar um erro.  
  
## <a name="remarks"></a>Comentários  
  
## <a name="see-also"></a>Consulte Também  
 [Configurar protocolos de cliente](https://technet.microsoft.com/library/ms181035.aspx)   
 [Configurando protocolos de cliente de servidor e bibliotecas de rede](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
