---
title: Тип xs:QName | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- xs:QName type
ms.assetid: 72c5bfde-b0b2-4372-bf36-97ba930dea06
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b8c251686085de410a3b0885a4e1755217ee6c2d
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58535086"
---
# <a name="the-xsqname-type"></a>Тип xs:QName
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает типы, унаследованные из **xs:QName** и использующие элемент ограничения XML-схемы. Кроме того, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в настоящее время не поддерживает типы объединений с **QName** в качестве типа элемента.  
  
## <a name="example"></a>Пример  
 Следующая инструкция `CREATE XML SCHEMA COLLECTION` не сможет загрузить XML-схему, так как указан тип `xs:QName` в качестве типа объединения:  
  
```  
CREATE XML SCHEMA COLLECTION QNameLimitation1 AS N'  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:simpleType name="myUnion">  
        <xs:union memberTypes="xs:int xs:QName"/>  
    </xs:simpleType>  
</xs:schema>'  
GO  
  
CREATE XML SCHEMA COLLECTION QNameLimitation2 AS N'  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:simpleType name="myUnion">  
        <xs:union memberTypes="xs:integer">  
   <xs:simpleType>  
    <xs:list itemType="xs:QName"/>  
   </xs:simpleType>  
  </xs:union>  
    </xs:simpleType>  
</xs:schema>'  
GO  
```  
  
 Обе инструкции потерпят неудачу с сообщением об ошибке.  
  
## <a name="see-also"></a>См. также  
 [Требования и ограничения для коллекций XML-схем на сервере](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
