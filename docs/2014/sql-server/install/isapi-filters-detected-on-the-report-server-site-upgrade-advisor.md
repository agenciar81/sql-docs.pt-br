---
title: Filtros ISAPI detectados no site do servidor de relatório (Supervisor de atualização) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- ISAPI filters
- report servers [Reporting Services], upgrade issues
ms.assetid: dd30560d-9e16-47c7-ba68-a9743a657e4e
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: a2b811955839eb22e3325d64c55454b92a6b1b8c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "71952439"
---
# <a name="isapi-filters-detected-on-the-report-server-site-upgrade-advisor"></a>Filtros ISAPI detectados no site do servidor de relatório (Supervisor de Atualização)
  O Supervisor de Atualização detectou um ou mais filtros ISAPI no site que hospeda o servidor de relatório e os diretórios virtuais do Gerenciador de Relatórios. Não há suporte para filtros ISAPI [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]no.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Forma.|  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>DESCRIÇÃO  
 Antes da atualização, verifique se os filtros ISAPI do site são usados por aplicativos do [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Se você não precisar do filtro ISAPI, poderá atualizar o servidor de relatório. A Instalação criará URLs padrão sem suporte para o filtro ISAPI executado no IIS. Se precisar do filtro ISAPI, não faça a atualização até encontrar uma maneira alternativa de hospedar o filtro ISAPI (por exemplo, usando o ISA Server ou continuando a hospedar o filtro ISAPI no IIS). O servidor de relatório suporta o ASP.NET HTTPModules como substituto dos filtros ISAPI em certos cenários. Para obter mais informações, consulte a documentação do ASP.NET sobre MSDN.  
  
## <a name="corrective-action"></a>Ação corretiva  
 Avalie e use uma solução separada para hospedar filtros ISAPI necessários para sua implantação.  
  
## <a name="see-also"></a>Consulte Também  
 [Problemas de atualização do Reporting Services &#40;o supervisor de atualização&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
