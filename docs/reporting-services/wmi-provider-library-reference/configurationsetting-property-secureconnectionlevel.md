---
title: "Свойство SecureConnectionLevel (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
apiname: SecureConnectionLevel
apilocation: reportingservices.mof
apitype: MOFDef
helpviewer_keywords: SecureConnectionLevel property
ms.assetid: fd5549e7-b874-41e2-866e-2f58caf6f733
caps.latest.revision: "19"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: be620ce014ce7357a23e20b0cbb61df79775a3b8
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="configurationsetting-property---secureconnectionlevel"></a>Свойство ConfigurationSetting — SecureConnectionLevel
  Возвращает уровень безопасного соединения, заданный в файле RSReportServer.config. Только для чтения.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Dim SecureConnectionLevel As Integer  
```  
  
```csharp  
public Integer SecureConnectionLevel;  
```  
  
## <a name="property-values"></a>Значения свойств  
 Значение **Integer** , представляющее уровень безопасного соединения. Возвращаемые значения указывают, была произведена настройка SSL или нет. Значение, которое больше или равно 1, указывает на то, что протокол SSL включен. Значение 0 указывает на то, что протокол SSL отключен.  
  
## <a name="example-code"></a>Пример кода  
 [Класс MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также раздел  
 [Элементы MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
