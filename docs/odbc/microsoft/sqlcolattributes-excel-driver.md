---
title: SQLColAttributes (driver do Excel) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Excel driver [ODBC], SQLColAttributes
- SQLColAttribute function [ODBC], Excel Driver
ms.assetid: 7c4833e3-ff0c-4313-9ab8-21379ceab656
author: MightyPen
ms.author: genemi
ms.openlocfilehash: cd3076ba19b9f5372074a9256e20d73858f69c09
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68132673"
---
# <a name="sqlcolattributes-excel-driver"></a>SQLColAttributes (Driver do Excel)
> [!NOTE]  
>  Este tópico fornece informações específicas do driver do Excel. Para obter informações gerais sobre essa função, consulte o tópico apropriado em [referência da API do ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Atributo|Comentários|  
|---------------|--------------|  
|SQL_COLUMN_DISPLAY_SIZE|Para dados LONGVARBINARY, SQL_COLUMN_DISPLAY_SIZE é o comprimento máximo da coluna, não o comprimento máximo da coluna vezes 2.|  
|SQL_OWNER_NAME|Uma cadeia de caracteres vazia ("") é retornada nesta coluna porque não há suporte para o nome do proprietário.|  
|SQL_QUALIFIER_NAME|O caminho para um diretório é retornado.|  
|SQL_COLUMN_SEARCHABLE|As colunas LONGVARBINARY e LONGVARCHAR são relatadas como SQL_UNSEARCHABLE.<br /><br /> Os tipos de dados Binary e Character de comprimento fixo e variável são pesquisáveis, mesmo que LONGVARBINARY e LONGVARCHAR não estejam.|  
  
> [!NOTE]  
>  O acima não é uma lista completa dos atributos retornados por **SQLColAttributes**.
