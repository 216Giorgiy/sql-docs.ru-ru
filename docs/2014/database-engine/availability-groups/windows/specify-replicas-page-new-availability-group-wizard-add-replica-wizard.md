---
title: Страница "Указание реплик" (мастер создания группы доступности/мастер добавления реплики) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.newagwizard.listeners.f1
- sql12.swb.newagwizard.specifyreplicas.f1
- sql12.swb.addreplicawizard.specifyreplicas.f1
ms.assetid: 2d90fc12-a67b-4bd0-b0ab-899b73017196
caps.latest.revision: 33
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a25a08e57395ca8523b29f976b93179e0989a8ac
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37279640"
---
# <a name="specify-replicas-page-new-availability-group-wizard-add-replica-wizard"></a>Укажите страницу реплик (мастер создания группы доступности: мастер добавления реплики)
  В этом разделе описываются параметры страницы **Выбор реплик** . Эта страница применяется к [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] и [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)] в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Страницу **Выбор реплик** можно использовать для настройки одной или нескольких реплик доступности и добавления ее в группу доступности. Эта страница содержит четыре вкладки, представленные в следующей таблице. Щелкните имя вкладки в таблице, чтобы перейти в соответствующий подраздел, далее в этом разделе.  
  
|Вкладка|Краткое описание|  
|---------|-----------------------|  
|[Реплики](#ReplicasTab)|С помощью этой вкладки можно задать все экземпляры [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , в которых будут или уже размещены вторичные реплики. Обратите внимание, что первичная реплика должна быть размещена на экземпляре сервера, с которым в данный момент установлено соединение.<br /><br /> Совет. Перед тем как перейти на другую вкладку, завершите задание всех реплик на вкладке **Реплики**.|  
|[Конечные точки](#EndpointsTab)|Эту вкладку можно использовать для проверки существующих конечных точек зеркального отображения баз данных, а также для их автоматического создания в случае, если они отсутствуют на экземпляре сервера, служба которого использует проверку подлинности Windows.|  
|[Параметры резервного копирования](#BackupPreferencesTab)|Эту вкладку можно использовать для задания настроек резервного копирования для группы доступности в целом, а также для задания приоритетов резервного копирования для отдельных реплик доступности.|  
|[Средство прослушивания](#Listener)|Если эта вкладка доступна, ее можно использовать для создания прослушивателя группы доступности. По умолчанию прослушиватель не создается.<br /><br /> Примечание. Эта вкладка доступна только при использовании [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)].|  
  
##  <a name="ReplicasTab"></a> Вкладка «Реплики»  
 **Экземпляр сервера**  
 Отображает имя экземпляра сервера, на котором будет размещена реплика доступности.  
  
 Если экземпляр сервера, используемый для размещения вторичной реплики, не перечислен в сетке **Реплики доступности** , нажмите кнопку **Добавить реплику** . При настройке группы доступности в гибридной ИТ-среде (см. [Высокая доступность и аварийное восстановление для SQL Server в виртуальных машинах Windows Azure](http://msdn.microsoft.com/library/windowsazure/jj870962.aspx)) можно нажать кнопку **Добавить реплику Azure** , чтобы создать виртуальные машины со вторичными репликами в Windows Azure.  
  
 **Первоначальная роль**  
 Указывает роль, которая изначально будет выполняться новой репликой: **Первичная** или **Вторичная**.  
  
 **Автоматическая отработка отказа (до 2)**  
 Установите этот флажок, только если вы хотите, чтобы реплика доступности стала партнером по автоматическому переходу на другой ресурс. Чтобы настроить автоматический переход на другой ресурс, необходимо выбрать этот параметр для первоначальной основной реплики и одной из вторичных реплик. В этих двух репликах будет использоваться режим доступности синхронной фиксации. Только две реплики могут поддерживать автоматический переход на другой ресурс.  
  
 Сведения о режиме доступности с синхронной фиксацией см. в разделе [режимы доступности (группы доступности AlwaysOn)](availability-modes-always-on-availability-groups.md). Сведения об автоматической отработке отказа см. в статье [Отработка отказа и режимы отработки отказа (группы доступности AlwaysOn)](failover-and-failover-modes-always-on-availability-groups.md).  
  
 **Синхронная фиксация (до 3).**  
 Если для реплики был выбран **Автоматическая отработка отказа (до 2)**, также будет выбрана **Синхронная фиксация (до 3)**. Если этот флажок не установлен, установить его следует, только если планируется использовать эту реплику в режиме синхронной фиксации только для запланированного перехода на другой ресурс вручную. Режим синхронной фиксации может использоваться только в трех репликах.  
  
 Если вы хотите, чтобы в этой реплике использовался режим доступности асинхронной фиксации, этот флажок устанавливать не следует. Реплика будет поддерживать только принудительный переход на другой ресурс (с возможной потерей данных). Сведения о режиме доступности с асинхронной фиксацией см. в разделе [режимы доступности (группы доступности AlwaysOn)](availability-modes-always-on-availability-groups.md). Сведения о запланированной отработке отказа вручную см. в статье [Отработка отказа и режимы отработки отказа (группы доступности AlwaysOn)](failover-and-failover-modes-always-on-availability-groups.md).  
  
 **Доступная для чтения вторичная роль**  
 Выберите значение в раскрывающемся списке **Доступная для чтения вторичная роль** следующим образом:  
  
 **Нет**  
 Прямые подключения для баз данных-получателей этой реплики не разрешаются. Для них не разрешен доступ для чтения. Это параметр по умолчанию.  
  
 **Назначение — только чтение**  
 Для баз данных-получателей этой реплики разрешены исключительно прямые подключения только для чтения. Для всех баз данных-получателей разрешен доступ для чтения.  
  
 **Да**  
 Для баз данных-получателей этой реплики разрешены все соединения, но только с доступом для чтения. Для всех баз данных-получателей разрешен доступ для чтения.  
  
 **Добавить реплику**  
 Выберите, чтобы добавить новую вторичную реплику в группу доступности.  
  
 **Добавить реплику Azure**  
 Щелкните здесь, чтобы создать виртуальную машину Windows Azure, на которой будет запущена вторичная реплика в группе доступности. Этот параметр применим только для группы доступности в гибридной ИТ-среде, содержащей локальные реплики. Дополнительные сведения см. в разделе [Высокая доступность и аварийное восстановление для SQL Server в виртуальных машинах Windows Azure](http://msdn.microsoft.com/library/windowsazure/jj870962.aspx).  
  
 **Удалить реплику**  
 Выберите, чтобы удалить выбранную вторичную реплику из группы доступности.  
  
##  <a name="EndpointsTab"></a> Вкладка «Конечные точки»  
 Для каждого экземпляра сервера, на котором будет размещаться реплика доступности, на вкладке **Конечные точки** отображаются фактические значения конечной точки зеркального отображения существующей базы данных (если таковая имеется) или предлагаемые значения для возможной новой конечной точки, в которой будет использоваться проверка подлинности Windows. И для существующих и для возможных конечных точек в сетке значений конечных точек отображается следующая информация.  
  
 **Имя сервера**  
 Отображает имя экземпляра сервера, на котором будет размещена реплика доступности.  
  
 **URL-адрес конечной точки**  
 Отображает фактический или предлагаемый URL-адрес конечной точки зеркального отображения базы данных. Для предлагаемой новой конечной точки это значение можно изменить. Сведения о формате этих URL-адресов см. в разделе [Указание URL-адреса конечной точки при добавлении или изменении реплики доступности (SQL Server)](specify-endpoint-url-adding-or-modifying-availability-replica.md).  
  
 **Номер порта**  
 Отображает фактический или предлагаемый номер порта конечной точки. Для предлагаемой новой конечной точки это значение можно изменить.  
  
 **Имя конечной точки**  
 Отображает фактическое или предлагаемое имя конечной точки. Для предлагаемой новой конечной точки это значение можно изменить.  
  
 **Шифрование данных**  
 Указывает, шифруются ли данные, отправляемые через эту конечную точку. Для предлагаемой новой конечной точки эту настройку можно изменить.  
  
 **Учетная запись службы SQL Server**  
 Имя пользователя учетной записи службы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
 Для обеспечения возможности использования экземпляром сервера конечной точки, для которой используется проверка подлинности Windows, его учетная запись службы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] должна быть учетной записью домена.  
  
 Это требование определяет следующий шаг конфигурации следующим образом.  
  
-   Если все экземпляры сервера запускаются под учетной записью службы домена, то есть если в столбце **Учетная запись службы SQL Server** отображается учетная запись службы домена для всех экземпляров серверов, нажмите кнопку **Далее**.  
  
-   Если какой-либо экземпляр сервера запускается под учетной записью, которая не является учетной записью службы домена, то необходимо вручную перейти на свой экземпляр сервера до продолжения работы с мастером. В этом случае при нажатии кнопки **Далее** отображается диалоговое окно предупреждения; необходимо нажать кнопку **Нет**, после чего будет выполнен возврат на вкладку**Конечные точки** . При выходе из мастера на странице **Выбор реплик** измените все экземпляры сервера, для которых в столбце **Учетная запись службы SQL Server** отображается учетная запись, не являющаяся записью службой домена, следующим образом.  
  
    -   Чтобы изменить учетную запись службы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] на учетную запись домена, используйте диспетчер конфигурации [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в статье [Изменение стартовой учетной записи службы для SQL Server (диспетчер конфигурации SQL Server)](../../configure-windows/scm-services-change-the-service-startup-account.md).  
  
    -   Используйте [!INCLUDE[tsql](../../../includes/tsql-md.md)] или PowerShell для создания вручную конечной точки зеркального отображения базы данных, использующей сертификат. Дополнительные сведения см. в статье [CREATE ENDPOINT (Transact-SQL)](/sql/t-sql/statements/create-endpoint-transact-sql) или [Создание конечной точки зеркального отображения базы данных для групп доступности AlwaysOn (SQL Server PowerShell)](database-mirroring-always-on-availability-groups-powershell.md).  
  
     Если страница **Выбор реплик доступности** была открыта во время настройки конечных точек, вернитесь на вкладку **Конечные точки** и нажмите кнопку **Обновить** , чтобы обновить сетку **Значения конечных точек** .  
  
##  <a name="BackupPreferencesTab"></a> Вкладка «Настройки резервного копирования»  
 Для указания места создания резервных копий выберите один из следующих параметров.  
  
 **Предпочтение вторичной**  
 Указывает, что резервное копирование должно выполняться на вторичной реплике, за исключением тех случаев, когда в режиме «в сети» находится только первичная реплика. В этом случае резервное копирование будет выполняться на первичной реплике. Это параметр по умолчанию.  
  
 **Только вторичная**  
 Указывает, что резервное копирование никогда не выполняется на первичной реплике. Если первичная реплика является единственной репликой, находящейся в режиме «в сети», резервное копирование не будет выполняться.  
  
 **Первичная**  
 Указывает, что резервное копирования должно всегда выполняться на первичной реплике. Данный параметр является полезным, если вам требуются такие функции резервного копирования, как создание разностных резервных копий, которые не поддерживаются при выполнении резервного копирования на вторичной реплике.  
  
 **Любая реплика**  
 Указывает, что вы предпочитаете, чтобы задания резервного копирования пропускали реплики доступности при выборе реплики для создания резервных копий. Примечание. Задания резервного копирования могут учитывать другие факторы, например приоритет резервного копирования каждой реплики доступности в сочетании с ее состоянием работоспособности и подключения.  
  
> [!IMPORTANT]  
>  Принудительного применения параметра приоритета резервного копирования не существует. Интерпретация данного приоритета зависит от логики (при ее наличии), которая внесена в задания резервного копирования для баз данных в указанной группе доступности. Дополнительные сведения см. в разделе [активные вторичные реплики: резервное копирование на вторичных репликах (группы доступности AlwaysOn)](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md).  
  
### <a name="replica-backup-priorities-grid"></a>Сетка приоритетов резервного копирования реплик  
 Сетку **Свойства резервного копирования реплик** можно использовать для указания приоритетов резервного копирования для каждой реплики в группе доступности. Сетка содержит следующие столбцы.  
  
 **Экземпляр сервера**  
 Отображает имя экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , на котором размещается реплика доступности.  
  
 **Приоритет резервного копирования (низкий = 1, высокий = 100)**  
 Задайте приоритет выполнения резервного копирования для данной реплики по отношению к другим репликам из той же группы доступности. Значение по умолчанию: 50. Можно выбрать любое число в диапазоне от 0 до 100. 1 указывает минимальный приоритет, 100 — наивысший приоритет. Если для параметра **Приоритет резервного копирования** задано значение 1, реплика доступности будет выбираться для создания резервных копий, только если реплики доступности с более высоким приоритетом в данный момент отсутствуют.  
  
 **Исключить реплику**  
 Предотвратить выбор реплики доступности при создании резервных копий. Этот параметр может быть полезным, например, для исключения удаленной реплики доступности, создание резервных копий на которой нежелательно.  
  
##  <a name="Listener"></a> Вкладка «Прослушиватель»  
 Выберите одну из следующих настроек для[прослушивателя группы доступности](../../listeners-client-connectivity-application-failover.md), предоставляющего точку подключения клиента:  
  
 **Создавать прослушиватель группы доступности не нужно.**  
 Выберите, чтобы пропустить этот шаг. Прослушиватель можно будет создать позже. Дополнительные сведения см. в разделе [Создание или настройка прослушивателя группы доступности (SQL Server)](create-or-configure-an-availability-group-listener-sql-server.md).  
  
 **Создание прослушивателя группы доступности.**  
 Задайте свойства прослушивателя для этой группы доступности следующим образом.  
  
 **DNS-имя прослушивателя**  
 Задайте сетевое имя прослушивателя. Имя должно быть уникальным для домена и может содержать только алфавитно-цифровые символы, дефисы (**-**) и символы подчеркивания (**_**). Если DNS-имя указывается на вкладке **Прослушиватель** , оно может содержать до 15 символов.  
  
> [!IMPORTANT]  
>  Если на вкладке **Прослушиватель** было введено недопустимое имя DNS-прослушивателя, то на странице **Выбор реплик** будет отключена кнопка **Далее** .  
  
 **Порт**  
 Задайте TCP-порт, используемый этим прослушивателем.  
  
> [!NOTE]  
>  Если на вкладке **Прослушиватель** был введен недопустимый номер порта (или DNS-имя прослушивателя), то на странице **Выбор реплик** будет отключена кнопка **Далее** .  
  
 **Сетевой режим**  
 Используйте этот раскрывающийся список, чтобы выбрать режим сети, который будет использоваться прослушивателем. Это может быть один из следующих режимов.  
  
 **Статический IP-адрес**  
 Выберите, если хотите, чтобы прослушиватель выполнял прослушивание более чем одной подсети. Для использования режима сети со статическими IP-адресами прослушиватель группы доступности должен выполнять прослушивание всех подсетей, в которых размещается реплика доступности для группы доступности. Для каждой подсети нажмите кнопку **Добавить** , чтобы выбрать адрес подсети и указать IP-адрес.  
  
 Если был выбран режим **Статические IP-адреса** (по умолчанию), в сетке будут отображены столбцы **Подсеть** и **IP-адрес** , а также кнопки **Добавить** и **Удалить** . Обратите внимание, что сетка будет пуста до тех пор, пока не будет добавлена первая подсеть.  
  
 Столбец**Подсеть**   
 Отображает адрес подсети, который был выбран для каждой подсети, добавленной для прослушивателя.  
  
 Столбец**IP-адрес**   
 Отображает адрес в формате IPv4 или IPv6, заданный для данной подсети.  
  
 **Добавить**  
 Нажмите, чтобы добавить подсеть для этого прослушивателя. Откроется диалоговое окно **Добавление IP-адреса** . Дополнительные сведения см. в разделе справки [Диалоговое окно "Добавление IP-адреса" (SQL Server Management Studio)](add-ip-address-dialog-box-sql-server-management-studio.md).  
  
 **Удалить**  
 Нажмите, чтобы удалить подсеть, выбранную в данный момент в сетке.  
  
 **DHCP**  
 Выберите, если необходимо, чтобы прослушиватель выполнял прослушивание одной подсети и использовал адрес в формате IPv4, заданный сервером, работающим с использованием протокола DHCP. Протокол DHCP имеет ограничение на работу только с одной подсетью. Такая ситуация часто присутствует на всех экземплярах сервера, на которых размещается реплика доступности для группы доступности.  
  
> [!IMPORTANT]  
>  Использовать протокол DHCP в производственной среде не рекомендуется. Если во время простоя аренда IP-адреса протокола DHCP истечет, то на регистрацию нового сетевого IP-адреса протокола DHCP, связанного с именем DNS-прослушивателя, уйдет дополнительное время, что скажется на производительности клиента. Однако протокол DHCP полезен при настройке среды разработки и проверки и позволяет проверить базовые функции групп доступности и их интеграцию с приложениями.  
  
 Если выбран протокол **DHCP** , будет отображено поле **Подсеть** .  
  
 **Подсеть**  
 Если был выбран режим сети **DHCP** , используйте раскрывающийся список **Подсеть** , чтобы выбрать адрес подсети, в которой размещены реплики доступности группы доступности.  
  
> [!IMPORTANT]  
>  После определения прослушивателя группы доступности настоятельно рекомендуется сделать следующее:  
>   
>  -   Попросите сетевого администратора зарезервировать IP-адрес, который будет использоваться только этим прослушивателем. Передайте имя узла DNS прослушивателя разработчикам приложения для использования в строке подключения при запросе клиентских соединений к данной группе доступности.  
> -   Передайте имя узла DNS прослушивателя разработчикам приложения для использования в строке подключения при запросе клиентских соединений к данной группе доступности.  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
  
-   [Использование мастера групп доступности (среда SQL Server Management Studio)](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Использование мастера добавления реплики в группу доступности (среда SQL Server Management Studio)](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Создание или настройка прослушивателя группы доступности (SQL Server)](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [Использование сертификатов для конечной точки зеркального отображения базы данных (Transact-SQL)](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
-   [CREATE ENDPOINT (Transact-SQL)](/sql/t-sql/statements/create-endpoint-transact-sql)  
  
-   [Создание базы данных конечной точки зеркального отображения для групп доступности AlwaysOn &#40;SQL Server PowerShell&#41;](database-mirroring-always-on-availability-groups-powershell.md)  
  
## <a name="see-also"></a>См. также  
 [Обзор групп доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [CREATE AVAILABILITY GROUP (Transact-SQL)](/sql/t-sql/statements/create-availability-group-transact-sql)   
 [Предварительные требования, ограничения и рекомендации для групп доступности AlwaysOn &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)  
  
  