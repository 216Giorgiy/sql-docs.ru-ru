---
title: "ALTER COLUMN ENCRYPTION KEY (Transact-SQL) | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 10/28/2015
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER COLUMN ENCRYPTION
- ALTER_COLUMN_ENCRYPTION_TSQL
- ALTER COLUMN ENCRYPTION KEY
- ALTER_COLUMN_ENCRYPTION_KEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- column encryption key, alter
- ALTER COLUMN ENCRYPTION KEY statement
ms.assetid: c79a220d-e178-4091-a330-c924cc0f0ae0
caps.latest.revision: 15
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6aaa1f85f860272cdb672d29bccdda39380f728a
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="alter-column-encryption-key-transact-sql"></a>ALTER COLUMN ENCRYPTION KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Изменяет ключ шифрования столбца в базе данных, добавления или удаления зашифрованного значения. Ключ CEK может иметь до двух значений, позволяющие для поворота соответствующий главный ключ столбца. Ключ CEK используется при шифровании столбцов с помощью [постоянного шифрования &#40; компонент Database Engine &#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md) компонентов. Перед добавлением в значение CEK, необходимо определить главный ключ столбца, который использовался для шифрования с помощью значения [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [CREATE MASTER KEY](../../t-sql/statements/create-column-master-key-transact-sql.md) инструкции.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
ALTER COLUMN ENCRYPTION KEY key_name   
    [ ADD | DROP ] VALUE   
    (  
        COLUMN_MASTER_KEY = column_master_key_name   
        [, ALGORITHM = 'algorithm_name' , ENCRYPTED_VALUE =  varbinary_literal ]   
    ) [;]  
```  
  
## <a name="arguments"></a>Аргументы  
 *key_name*  
 Ключ шифрования столбца, которое требуется изменить.  
  
 *column_master_key_name*  
 Указывает имя главного ключа столбца (CMK) используется для шифрования ключа шифрования столбца (CEK).  
  
 *algorithm_name*  
 Имя алгоритма шифрования, используемого для шифрования значение. Этот алгоритм для системных поставщиков должен быть **RSA_OAEP**. Этот аргумент является недопустимым, при удалении значения ключа шифрования столбца.  
  
 *varbinary_literal*  
 Большой двоичный объект ключа CEK зашифрован с указанным шаблоном ключа шифрования. . Этот аргумент является недопустимым, при удалении значения ключа шифрования столбца.  
  
> [!WARNING]  
>  Никогда не передавать открытого текста CEK значения в этой инструкции. Таким образом будет составляют преимуществ этой возможности.  
  
## <a name="remarks"></a>Замечания  
 Как правило ключ шифрования столбца создается с одной зашифрованное значение. Когда главный ключ столбца должен быть повернуты (текущий столбец главный ключ должен заменяться нового главного ключа столбца), можно добавить новое значение ключа шифрования столбца, зашифрованные с помощью нового главного ключа столбца. Это позволит убедиться, что клиентские приложения могут обращаться к данные, зашифрованные с помощью ключа шифрования столбца, пока новый главный ключ столбца становится доступной для клиентских приложений. Постоянное шифрование включено драйвера в клиентское приложение, которое не имеет доступа к новым главным ключом, будут иметь возможность использовать значения ключа шифрования столбца зашифрованы с помощью старого главного ключа столбца для доступа к конфиденциальным данным. Алгоритмы шифрования, постоянное шифрование поддерживает, требуется значение открытого текста, чтобы иметь 256 бит. Зашифрованное значение должны быть созданы с помощью поставщика хранилища ключей, который инкапсулирует хранилище ключей, содержащее главный ключ столбца.  
  
 Используйте [sys.columns &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md), [sys.column_encryption_keys &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-column-encryption-keys-transact-sql.md) и [sys.column_encryption_key_values &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-column-encryption-key-values-transact-sql.md) для просмотра сведений о ключах шифрования столбцов.  
  
## <a name="permissions"></a>Permissions  
 Требуется **ALTER ANY COLUMN ENCRYPTION KEY** разрешения в базе данных.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-adding-a-column-encryption-key-value"></a>A. Добавление значения ключа шифрования столбца  
 В следующем примере изменяется ключ шифрования столбца с именем `MyCEK`.  
  
```  
ALTER COLUMN ENCRYPTION KEY MyCEK  
ADD VALUE  
(  
    COLUMN_MASTER_KEY = MyCMK2,   
    ALGORITHM = 'RSA_OAEP',   
    ENCRYPTED_VALUE = 0x016E000001630075007200720065006E00740075007300650072002F006D0079002F0064006500650063006200660034006100340031003000380034006200350033003200360066003200630062006200350030003600380065003900620061003000320030003600610037003800310066001DDA6134C3B73A90D349C8905782DD819B428162CF5B051639BA46EC69A7C8C8F81591A92C395711493B25DCBCCC57836E5B9F17A0713E840721D098F3F8E023ABCDFE2F6D8CC4339FC8F88630ED9EBADA5CA8EEAFA84164C1095B12AE161EABC1DF778C07F07D413AF1ED900F578FC00894BEE705EAC60F4A5090BBE09885D2EFE1C915F7B4C581D9CE3FDAB78ACF4829F85752E9FC985DEB8773889EE4A1945BD554724803A6F5DC0A2CD5EFE001ABED8D61E8449E4FAA9E4DD392DA8D292ECC6EB149E843E395CDE0F98D04940A28C4B05F747149B34A0BAEC04FFF3E304C84AF1FF81225E615B5F94E334378A0A888EF88F4E79F66CB377E3C21964AACB5049C08435FE84EEEF39D20A665C17E04898914A85B3DE23D56575EBC682D154F4F15C37723E04974DB370180A9A579BC84F6BC9B5E7C223E5CBEE721E57EE07EFDCC0A3257BBEBF9ADFFB00DBF7EF682EC1C4C47451438F90B4CF8DA709940F72CFDC91C6EB4E37B4ED7E2385B1FF71B28A1D2669FBEB18EA89F9D391D2FDDEA0ED362E6A591AC64EF4AE31CA8766C259ECB77D01A7F5C36B8418F91C1BEADDD4491C80F0016B66421B4B788C55127135DA2FA625FB7FD195FB40D90A6C67328602ECAF3EC4F5894BFD84A99EB4753BE0D22E0D4DE6A0ADFEDC80EB1B556749B4A8AD00E73B329C95827AB91C0256347E85E3C5FD6726D0E1FE82C925D3DF4A9  
);  
GO  
  
```  
  
### <a name="b-dropping-a-column-encryption-key-value"></a>Б. Удаление значения ключа шифрования столбца  
 В следующем примере изменяется ключ шифрования столбца с именем `MyCEK` , удалив значение.  
  
```  
ALTER COLUMN ENCRYPTION KEY MyCEK  
DROP VALUE  
(  
    COLUMN_MASTER_KEY = MyCMK  
);  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [CREATE COLUMN ENCRYPTION KEY (Transact-SQL)](../../t-sql/statements/create-column-encryption-key-transact-sql.md)   
 [УДАЛИТЬ ключ ШИФРОВАНИЯ СТОЛБЦА &#40; Transact-SQL &#41;](../../t-sql/statements/drop-column-encryption-key-transact-sql.md)   
 [CREATE COLUMN MASTER KEY (Transact-SQL)](../../t-sql/statements/create-column-master-key-transact-sql.md)   
 [Постоянное шифрование (компонент Database Engine)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
 [sys.column_encryption_keys (Transact-SQL)](../../relational-databases/system-catalog-views/sys-column-encryption-keys-transact-sql.md)   
 [sys.column_encryption_key_values (Transact-SQL)](../../relational-databases/system-catalog-views/sys-column-encryption-key-values-transact-sql.md)   
 [sys.columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)  
  
  
