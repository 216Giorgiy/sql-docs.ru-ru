---
title: Свойство Detail | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Detail property
- SoapException class
ms.assetid: c1ddaeb6-c540-49fa-b06e-b6359d377ee8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 27d9d7ab4cd29c6eb0ea7ae1c6bddbe8c1b7ef06
ms.sourcegitcommit: b87c384e10d6621cf3a95ffc79d6f6fad34d420f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60158820"
---
# <a name="detail-property"></a>Свойство Detail
  Свойство **Detail** класса [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]SoapException**служб** имеет следующую структуру XML:  
  
## <a name="elements"></a>Элементы  
 **Detail**  
 Элемент верхнего уровня, содержащий все остальные элементы данных об ошибке.  
  
 **ErrorCode**  
 Код ошибки служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 **HttpStatus**  
 Код состояния HTTP.  
  
 **Сообщение**  
 Сообщение об ошибке и код ошибки, присвоенный сервером отчетов.  
  
 **HelpLink**  
 URL-адрес справочной ссылки на веб-сайт, где находятся дополнительные сведения об ошибке. Дополнительные сведения см. в разделе [Элемент HelpLink](helplink-element.md).  
  
 **LinkID**  
 Идентификатор, присвоенный ссылке.  
  
 **ProductName**  
 Имя продукта. Значение по умолчанию — **Microsoft SQL Server Reporting Services**.  
  
 **ProductVersion**  
 Версия служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Максимальная длина составляет 15 символов. Формат номера версии должен иметь следующий вид: 8.00.0xxx.00.  
  
 **ProductLocaleId**  
 Идентификатор локали или идентификатор языка библиотеки INTL приложения (например, 0x41A).  
  
 **OperatingSystem**  
 Операционная система, в которой установлены службы [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Допустимыми являются значение **0** (независимость от операционной системы), значение **1** ([!INCLUDE[win2kfamily](../../../includes/win2kfamily-md.md)]) и значение **16** (Windows XP).  
  
 **CountryLocaleId**  
 Идентификатор локали или идентификатор языка операционной системы. Например, для французской версии Windows используется значение 0x040c.  
  
 **MoreInformation**  
 XML-строка, содержащая вложенные исключения, сформированные во время выполнения метода.  
  
 **Source**  
 Дочерний элемент для элемента **MoreInformation**. Источник ошибки.  
  
 **Сообщение**  
 Дочерний элемент для элемента **MoreInformation**. Сообщение ошибки для вложенного исключения. Этот элемент включает XML-атрибуты для элементов **ErrorCode** и **HelpLink**.  
  
 **Предупреждения**  
 XML-строка, содержащая предупреждения, возвращенные при обработке отчета.  
  
## <a name="see-also"></a>См. также  
 [Введение в обработку исключений в службах Reporting Services](../introducing-exception-handling-in-reporting-services.md)   
 [Класс SoapException в службах Reporting Services](reporting-services-soapexception-class.md)   
 [Использование свойства Detail для обработки определенных ошибок](../best-practices/using-the-detail-property-to-handle-specific-errors.md)  
  
  
