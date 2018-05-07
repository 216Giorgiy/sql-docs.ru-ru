---
title: srv_sendrow (интерфейс API расширенных хранимых процедур) | Документы Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: extended-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- srv_sendrow
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_sendrow
ms.assetid: a08f608a-10e6-4bff-9b48-0d02e8026cdb
caps.latest.revision: 31
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: c580be2c140464b98900453349cae80079772275
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="srvsendrow-extended-stored-procedure-api"></a>srv_sendrow (API-интерфейс расширенных хранимых процедур)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Используйте вместо этого интеграцию со средой CLR.  
  
 Передает строку данных на клиент.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
int srv_sendrow ( SRV_PROC *  
srvproc   
);  
```  
  
## <a name="arguments"></a>Аргументы  
 *srvproc*  
 Указатель на структуру SRV_PROC, который представляет собой дескриптор соединения с клиентом (в данном случае — дескриптор, который получил запрос языка). Структура содержит сведения, которые используются библиотекой API-интерфейса расширенных хранимых процедур для управления связью и передачи данных между приложением и клиентом.  
  
## <a name="returns"></a>Возвращает  
 SUCCEED или FAIL.  
  
## <a name="remarks"></a>Remarks  
 Функция **srv_sendrow** вызывается по разу для каждой из строк, отправляемых клиенту. Все строки должны быть отправлены клиенту до того, как будут отправлены любые сообщения, значения состояния или состояние завершения с помощью функций **srv_sendmsg**, **srv_status**или **srv_senddone**.  
  
 При отправке строки, для которой не все столбцы определены с помощью функции **srv_describe** , API-интерфейс расширенных хранимых процедур выдаст информационное сообщение об ошибке и вернет клиенту значение FAIL. В этом случае строка не отправляется.  
  
> [!NOTE]  
>  API-интерфейс расширенных хранимых процедур не поддерживает отправку клиенту вычисляемых строк. Кроме того, если клиенту отправляется строка данных, содержащая **ntext**, **text**или **image** , то в нее не включаются текстовый указатель и текстовая отметка времени.  
  
> [!IMPORTANT]  
>  Необходимо тщательно просмотреть исходный код расширенных хранимых процедур и проверить скомпилированные библиотеки DLL перед их установкой на рабочий сервер. Сведения о проверке безопасности см. на следующем [веб-сайте Майкрософт](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>См. также:  
 [srv_describe (интерфейс API расширенных хранимых процедур)](../../relational-databases/extended-stored-procedures-reference/srv-describe-extended-stored-procedure-api.md)  
  
  