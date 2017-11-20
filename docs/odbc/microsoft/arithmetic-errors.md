---
title: "Арифметические ошибки | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- arithmetic errors [ODBC]
- desktop database drivers [ODBC], arithmetic errors
ms.assetid: 1c47bfac-7455-4487-b673-6b47d2a2d756
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9d3585f6e1be7a3f9451231004979321202d7852
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="arithmetic-errors"></a>Арифметические ошибки
Драйвер ODBC вычисляет предложения WHERE в инструкции SELECT, он извлекает каждую строку. Если строка содержит значение, которое вызывает арифметическую ошибку переполнения, деления на ноль или numeric, например, драйвер возвращает все строки, но возвращает ошибки для столбцов с помощью арифметических ошибок. При вставке или обновлении, однако драйвер ODBC останавливается, вставка или обновление данных при обнаружении первой ошибки арифметического.

