---
title: Занятие 2. Задание информации о соединении (службы Reporting Services) | Документация Майкрософт
ms.date: 05/23/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.assetid: 54405a3a-d7fa-4d95-8963-9aa224e5901e
author: markingmyname
ms.author: maghan
ms.openlocfilehash: da47a0fd587d48dd9d932504d6a5cd45d0d54664
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2019
ms.locfileid: "56294702"
---
# <a name="lesson-2-specifying-connection-information-reporting-services"></a>Занятие 2. Задание информации о строке соединения (службы Reporting Services)
После добавления разбитого на страницы отчета [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] к проекту Tutorial на занятии 1 следует задать *источник данных*, который представляет собой сведения о соединении, используемые отчетом для доступа к данным, которые располагаются в реляционной базе данных, многомерной базе данных или ином источнике.  
  
В этом занятии в качестве источника данных используется образец базы данных [!INCLUDE[ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)]. В учебнике предполагается, что эта база данных находится в экземпляре [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] по умолчанию, установленном на локальном компьютере.  
  
### <a name="to-set-up-a-connection"></a>Настройка соединения  
  
1.  В области **данных отчета** нажмите кнопку **Создать** и выберите **Data Source**.  
Если область **Данные отчета** не отображается, в меню **Вид** выберите пункт **Данные отчета**.  

    ![ssrs-table-tutorial-2-new-data-source](../reporting-services/media/ssrs-table-tutorial-2-new-data-source.png)
  
   2.  В поле **Имя**введите *AdventureWorks2014*.  
  
3.  Убедитесь в том, что выбран параметр **Внедренное соединение** .  
  
4.  В поле **Тип**выберите **Microsoft SQL Server**.  
  
5.  В поле **Строка подключения**введите следующее:  
  
    ```  
    Data source=localhost; initial catalog=AdventureWorks2014  
    ```  
  
     Эта строка соединения подразумевает, что на локальном компьютере установлены среда [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], сервер отчетов и база данных [!INCLUDE[ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)] , а у пользователя имеется разрешение на подключение к базе данных [!INCLUDE[ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)] . Если ваша база данных AdventureWorks2014 находится не на локальном компьютере, измените строку подключения, заменив *loclahost* на имя своего экземпляра сервера баз данных.
  
     >[!NOTE]  
    >В случае использования версии [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services или именованного экземпляра строка соединения должна включать сведения об экземпляре:  
    >  
    >`Data source=localhost\SQLEXPRESS; initial catalog=AdventureWorks2014`  
    >  
    >Дополнительные сведения о строках подключения см. в следующих разделах: [Подключения данных, Источники данных и Строки подключения в службе Reporting Services](../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md).  
     
  
6.  На панели слева щелкните **Учетные данные** и выберите **Использовать проверку подлинности Windows (встроенная безопасность)**.  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)] Источник данных **AdventureWorks2014** появляется в области **данных отчета** .  
![ssrs_adventureworks_datasource](../reporting-services/media/ssrs-adventureworks-datasource.png)  
## <a name="next-task"></a>Следующая задача  
Соединение с образцом базы данных [!INCLUDE[ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)] успешно создано. Далее предстоит создать отчет. См. [Занятие 3. Определение набора данных для табличного отчета (службы Reporting Services)](../reporting-services/lesson-3-defining-a-dataset-for-the-table-report-reporting-services.md).  
  
## <a name="see-also"></a>См. также:  
[Подключения данных, Источники данных и Строки подключения в службе Reporting Services](../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)  
  
  
  

