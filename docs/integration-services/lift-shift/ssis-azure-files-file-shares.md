---
title: "Хранение файлов в общих папках в локальной среде и в Azure и их извлечение | Документы Майкрософт"
description: "В этой статье описывается использование файловой системы и общих папок в локальной среде и в Azure со службами SQL Server Integration Services"
ms.date: 11/27/2017
ms.topic: article
ms.prod: sql-non-specified
ms.technology: integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5b6034787f2e6ab34e583c06d219d7415c82d055
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2017
---
# <a name="store-and-retrieve-files-on-file-shares-on-premises-and-in-azure-with-ssis"></a>Хранение файлов в общих папках в локальной среде и в Azure и их извлечение
В этой статье описывается, как обновить пакеты служб SQL Server Integration Services (SSIS), использующие локальную файловую систему, при их переносе в службы SSIS в Azure.

> [!IMPORTANT]
> В настоящее время база данных каталога SSIS (SSISDB) поддерживает только один набор учетных данных для доступа. Поэтому инфраструктура Azure-SSIS Integration Runtime (IR) не может использовать разные учетные данные для подключения к нескольким локальным общим папкам и общим папкам в службе файлов Azure.

## <a name="store-temporary-files"></a>Хранение временных файлов
Если при выполнении отдельного пакета необходимо хранить и обрабатывать временные файлы, для пакетов можно использовать текущую рабочую папку `.` или временную папку `%TEMP%` на узлах Azure-SSIS Integration Runtime.

## <a name="store-files-across-multiple-package-executions"></a>Хранение файлах в рамках нескольких операций выполнения пакетов
Если постоянные файлы необходимо хранить и обрабатывать в рамках нескольких операций выполнения пакетов, можно использовать локальные общие папки или службу файлов Azure.

### <a name="use-on-premises-file-shares"></a>Использование локальных общих папок
Чтобы и далее применять **локальные общие папки** при переносе пакетов, использующих локальные файловые системы, в службы SSIS в Azure, выполните указанные ниже действия.
1.  Перенесите файлы из локальных файловых систем в локальные общие папки.
2.  Присоедините локальные общие папки к виртуальной сети Azure.
3.  Присоедините среду Azure-SSIS IR к той же виртуальной сети. Дополнительные сведения см. в разделе [Присоединение среды выполнения интеграции Azure SSIS к виртуальной сети](https://docs.microsoft.com/azure/data-factory/join-azure-ssis-integration-runtime-virtual-network).
4.  Подключите среду Azure-SSIS IR к локальным общим папкам в той же виртуальной сети, настроив учетные данные для доступа с проверкой подлинности Windows. Дополнительные сведения см. в разделе [Подключение к локальным источникам данных и общим папкам Azure с помощью проверки подлинности Windows](ssis-azure-connect-with-windows-auth.md).
5.  Измените локальные пути к файлам в пакетах на UNC-пути, указывающие на локальные общие папки. Например, измените `C:\abc.txt` на `\\<on-prem-server-name>\<share-name>\abc.txt`.

### <a name="use-azure-file-shares"></a>Использование общих папок Azure
Чтобы применять службу **Файлы Azure** при переносе пакетов, использующих локальные файловые системы, в службы SSIS в Azure, выполните указанные ниже действия.
1.  Перенесите файлы из локальных файловых систем в службы файлов Azure. Дополнительные сведения см. на странице [Файлы Azure](https://azure.microsoft.com/services/storage/files/).
2.  Подключите среду Azure-SSIS IR к службе файлов Azure, настроив учетные данные для доступа с проверкой подлинности Windows. Дополнительные сведения см. в разделе [Подключение к локальным источникам данных и общим папкам Azure с помощью проверки подлинности Windows](ssis-azure-connect-with-windows-auth.md).
3.  Измените локальные пути к файлам в пакетах на UNC-пути, указывающие на службу файлов Azure. Например, измените `C:\abc.txt` на `\\<storage-account-name>.file.core.windows.net\<share-name>\abc.txt`.