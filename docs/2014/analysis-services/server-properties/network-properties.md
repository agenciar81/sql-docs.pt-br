---
title: Propriedades da rede | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- LingerTimeout property
- EnableNagleAlgorithm property
- MinPendingAcceptExCount property
- MaxPendingSendCount property
- EnableBinaryXML property
- MinPendingReceiveCount property
- MaxCompletedReceiveCount property
- DisableNonblockingMode property
- RequestSizeThreshold property
- CompressionLevel property
- ReceiveBufferSize property
- EnableCompression property
- ServerSendTimeout property
- IPV4Support property
- MaxPendingReceiveCount property
- MaxPendingAcceptExCount property
- IPV6Support property
- MaxAllowedRequestSize property
- ServerReceiveTimeout property
- EnableLingerOnClose property
- InitialConnectTimeout property
- SendBufferSize property
- ScatterReceiveMultiplier property
- network properties [Analysis Services]
ms.assetid: ef4251e2-abe5-4c5b-9868-7549782d0244
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 882b5fc60020423e19f68fda40273b7c944bd4f5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66068881"
---
# <a name="network-properties"></a>Propriedades de rede
  
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] oferece suporte às propriedades do servidor listadas nas tabelas a seguir. Para obter mais informações sobre as propriedades de servidor adicionais e como defini-las, consulte [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).  
  
 **Aplica-se a:** Modo de servidor multidimensional e tabular  
  
## <a name="general"></a>Geral  
 `ListenOnlyOnLocalConnections`  
 Uma propriedade Booleana que identifica a escuta apenas em conexões locais, por exemplo localhost.  
  
## <a name="listener"></a>Ouvinte  
 `IPV4Support`  
 Uma propriedade de inteiro de 32 bits assinada que define o suporte ao protocolo IPv4. Essa propriedade tem um dos valores listados na tabela a seguir:  
  
|Valor|DESCRIÇÃO|  
|-----------|-----------------|  
|*0*|IPv4 desabilitado; os clientes não podem se conectar.|  
|*1*|(Padrão) IPv4 necessário; servidor não será iniciado se não puder escutar IPv4.|  
|*2*|IPv4 é opcional; o servidor tenta escutar IPv4, mas será iniciado mesmo se não conseguir.|  
  
 `IPV6Support`  
 Uma propriedade de inteiro de 32 bits assinada que define o suporte ao protocolo IPv6. Essa propriedade tem um dos valores listados na tabela a seguir:  
  
|Valor|DESCRIÇÃO|  
|-----------|-----------------|  
|*0*|IPv6 desabilitado; os clientes não podem se conectar.|  
|*1*|(Padrão) IPv6 necessário; servidor não será iniciado se não for possível escutar IPv6|  
|*2*|IPv6 é opcional; o servidor tenta escutar IPv6, mas será iniciado mesmo se não conseguir.|  
  
 `MaxAllowedRequestSize`  
 Uma propriedade avançada que não deve ser alterada, exceto sob orientação do suporte da [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `RequestSizeThreshold`  
 Uma propriedade avançada que não deve ser alterada, exceto sob orientação do suporte da [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `ServerReceiveTimeout`  
 Uma propriedade avançada que não deve ser alterada, exceto sob orientação do suporte da [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `ServerSendTimeout`  
 Uma propriedade avançada que não deve ser alterada, exceto sob orientação do suporte da [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="requests"></a>Requests  
 `EnableBinaryXML`  
 Uma propriedade Booleana que especifica se o servidor reconhecerá solicitações xml em formato binário.  
  
 `EnableCompression`  
 Uma propriedade Booleana que especifica se a compressão está habilitada para solicitações.  
  
## <a name="responses"></a>Respostas  
 `CompressionLevel`  
 Uma propriedade avançada que não deve ser alterada, exceto sob orientação do suporte da [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `EnableBinaryXML`  
 Uma propriedade Booleana que especifica se o servidor está habilitado para respostas xml binárias.  
  
 `EnableCompression`  
 Uma propriedade Booleana que especifica se a compressão está habilitada para respostas a solicitações de cliente.  
  
## <a name="tcp"></a>TCP  
 `InitialConnectTimeout`  
 Uma propriedade avançada que não deve ser alterada, exceto sob orientação do suporte da [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `MaxCompletedReceiveCount`  
 Uma propriedade avançada que não deve ser alterada, exceto sob orientação do suporte da [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `MaxPendingAcceptExCount`  
 Uma propriedade avançada que não deve ser alterada, exceto sob orientação do suporte da [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `MaxPendingReceiveCount`  
 Uma propriedade avançada que não deve ser alterada, exceto sob orientação do suporte da [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `MaxPendingSendCount`  
 Uma propriedade avançada que não deve ser alterada, exceto sob orientação do suporte da [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `MinPendingAcceptExCount`  
 Uma propriedade avançada que não deve ser alterada, exceto sob orientação do suporte da [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `MinPendingReceiveCount`  
 Uma propriedade avançada que não deve ser alterada, exceto sob orientação do suporte da [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `ScatterReceiveMultiplier`  
 Uma propriedade avançada que não deve ser alterada, exceto sob orientação do suporte da [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `SocketOptions\ DisableNonblockingMode`  
 Uma propriedade avançada que não deve ser alterada, exceto sob orientação do suporte da [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `SocketOptions\ EnableLingerOnClose`  
 Uma propriedade avançada que não deve ser alterada, exceto sob orientação do suporte da [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `SocketOptions\EnableNagleAlgorithm`  
 Uma propriedade avançada que não deve ser alterada, exceto sob orientação do suporte da [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `SocketOptions\ LingerTimeout`  
 Uma propriedade avançada que não deve ser alterada, exceto sob orientação do suporte da [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `SocketOptions\ ReceiveBufferSize`  
 Uma propriedade avançada que não deve ser alterada, exceto sob orientação do suporte da [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `SocketOptions\ SendBufferSize`  
 Uma propriedade avançada que não deve ser alterada, exceto sob orientação do suporte da [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="see-also"></a>Consulte Também  
 [Configurar propriedades do servidor no Analysis Services](server-properties-in-analysis-services.md)   
 [Determinar o modo de servidor de uma instância de Analysis Services](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
