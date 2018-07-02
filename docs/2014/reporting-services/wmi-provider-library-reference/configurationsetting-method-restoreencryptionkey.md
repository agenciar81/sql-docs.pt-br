---
title: Método RestoreEncryptionKey (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
api_name:
- RestoreEncryptionKey (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- RestoreEncryptionKey method
ms.assetid: 37e949f5-15af-4858-848a-f482ee94fcd9
caps.latest.revision: 18
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: d6ac5da7c9867b7ce84c9f29bfe82f905d5c626a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36009686"
---
# <a name="restoreencryptionkey-method-wmi-msreportserverconfigurationsetting"></a>Método RestoreEncryptionKey (WMI MSReportServer_ConfigurationSetting)
  Reaplica a chave de criptografia especificada para o banco de dados do servidor de relatório.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
Public Sub RestoreEncryptionKey(ByRef KeyFile() As Integer, _  
    ByRef Length As Int32, ByVal Password As String, _  
    ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void RestoreEncryptionKey(out Byte[] KeyFile, out Int32 Length,   
            string Password, out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a>Parâmetros  
 *KeyFile[]*  
 [fora] Uma matriz que contém a chave de criptografia criptografada.  
  
 *Comprimento*  
 [fora] O tamanho da matriz retornada pelo método.  
  
 *Senha*  
 Uma cadeia de caracteres usada para criptografar a chave de criptografia.  
  
 *HRESULT*  
 [out] Valor que indica se a chamada obteve êxito ou falhou.  
  
 *ExtendedErrors[]*  
 [fora] Uma matriz de cadeia de caracteres que contém erros adicionais retornados pela chamada.  
  
## <a name="return-value"></a>Valor retornado  
 Retorna um *HRESULT* indicando êxito ou falha da chamada do método. Um valor 0 indica que a chamada do método teve êxito. Um valor diferente de zero indica que ocorreu um erro.  
  
## <a name="remarks"></a>Remarks  
 Se uma entrada já existir para o servidor de relatório no banco de dados do servidor de relatório, ela será excluída. A nova entrada será criada com a chave de criptografia especificada e a chave pública do servidor de relatório.  
  
 O método é mais eficaz quando chamado depois de [DeleteEncryptionKey](configurationsetting-method-deleteencryptionkey.md) método, que limpa a lista de chaves de criptografia.  
  
## <a name="requirements"></a>Requisitos  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Membros de MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  