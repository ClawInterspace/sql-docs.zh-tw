---
title: restorefilegroup （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- restorefilegroup_TSQL
- restorefilegroup
dev_langs:
- TSQL
helpviewer_keywords:
- filegroups [SQL Server], restorefilegroup system table
- restorefilegroup system table
ms.assetid: 3aa15c55-6b72-4f76-97d7-bd88391d105c
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 74e3e445af4ffe9db6ede0d0e5fb3f457317fbd0
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85881443"
---
# <a name="restorefilegroup-transact-sql"></a>restorefilegroup (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  針對每個還原的檔案群組，各包含一個資料列。 此資料表會儲存在**msdb**資料庫中。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**restore_history_id**|**int**|用來識別對應的還原作業的唯一識別碼。 參考**restorehistory （restore_history_id）**。|  
|**filegroup_name**|**nvarchar(128)**|正在還原的檔案群組名稱。 可以是 NULL。<br /><br /> 當資料庫還原為資料庫快照集時，會依照完整還原的相同方式來擴展這個值。|  
  
## <a name="remarks"></a>備註  
 若要減少此資料表以及其他備份和記錄資料表中的資料列數目，請執行[sp_delete_backuphistory](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md)預存程式。  
  
## <a name="see-also"></a>另請參閱  
 [備份和還原資料表 &#40;Transact-sql&#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)   
 [restorefile &#40;Transact-sql&#41;](../../relational-databases/system-tables/restorefile-transact-sql.md)   
 [restorehistory &#40;Transact-sql&#41;](../../relational-databases/system-tables/restorehistory-transact-sql.md)   
 [系統資料表 &#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
