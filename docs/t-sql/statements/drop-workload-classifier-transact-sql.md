---
title: Классификатор DROP WORKLOAD (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/13/2019
ms.prod: sql
ms.prod_service: sql-data-warehouse
ms.reviewer: jrasnick
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- WORKLOAD CLASSIFIER
- WORKLOAD_CLASSIFIER_TSQL
- DROP_WORKLOAD_CLASSIFIER_TSQL
- DROP WORKLOAD GROUP
dev_langs:
- TSQL
helpviewer_keywords:
- DROP WORKLOAD CLASSIFIER statement
ms.assetid: ''
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: =azure-sqldw-latest||=sqlallproducts-allversions
ms.openlocfilehash: a9ef53323d77f1439df5daf0fedc669fe380cb3f
ms.sourcegitcommit: 46a2c0ffd0a6d996a3afd19a58d2a8f4b55f93de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/15/2019
ms.locfileid: "59581518"
---
# <a name="drop-workload-classifier-transact-sql-preview"></a>Классификатор DROP WORKLOAD (Transact-SQL) (Предварительная версия)

> [!Note]
> Классификация рабочих нагрузок доступна в предварительной версии в Хранилище данных SQL 2-го поколения. Предварительные версии таких функций, как управленческая классификация рабочих нагрузок и приоритет рабочих нагрузок доступны в сборках, выпущенных после 9 апреля 2019 г.  Чтобы протестировать функцию управления рабочими нагрузками, следует использовать сборки, выпущенные после этой даты.  Чтобы узнать номер своей версии Хранилища данных SQL, выполните команду SELECT @@version при подключении к экземпляру Хранилища данных SQL.

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Удаляет существующий определяемый пользователем классификатор рабочей нагрузки управления.  
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  

```
DROP WORKLOAD CLASSIFIER classifier_name;
```

## <a name="arguments"></a>Аргументы

*classifier_name*  
Указывает имя, по которому идентифицируется классификатор рабочей нагрузки.  Значение classifier_name — это sysname.  Оно может иметь длину до 128 символов и должно быть уникальным в пределах экземпляра.
  
## <a name="remarks"></a>Remarks

Инструкция DROP WORKLOAD CLASSIFIER не допускается для системных классификаторов рабочей нагрузки.

Если запросы выполняются или находятся в очереди запросов в приостановленном состоянии, они сохраняют свою классификацию и классификатор может быть удален немедленно.  Удаление и повторное создание классификатора с другим уровнем важности не затрагивает уже классифицированные запросы.

## <a name="permissions"></a>Разрешения

Необходимо разрешение CONTROL DATABASE.  
  
## <a name="examples"></a>Примеры

В следующем примере удаляется классификатор рабочей нагрузки с именем `wgcELTROLE`.  

```sql
DROP WORKLOAD CLASSIFIER wgcELTRole;
```

> [!NOTE]
> Запрос, отправленный без соответствующего классификатора, классифицируется в группу рабочей нагрузки по умолчанию.  Группа рабочей нагрузки по умолчанию — класс ресурсов smallrc.
  
## <a name="see-also"></a>См. также:

[CREATE WORKLOAD CLASSIFIER &#40;Transact-SQL&#41;](../../t-sql/statements/create-workload-classifier-transact-sql.md)</br>
[Классификация рабочих нагрузок хранилища данных SQL](/azure/sql-data-warehouse/sql-data-warehouse-workload-classification)
