---
title: sp_delete_targetservergroup （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_targetservergroup_TSQL
- sp_delete_targetservergroup
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_targetservergroup
ms.assetid: d8dd838e-64aa-419f-9ccb-ff04908cf3e4
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 2d6f00cf5fcc0cad2c5b6874b7302d00655e7a76
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85862365"
---
# <a name="sp_delete_targetservergroup-transact-sql"></a>sp_delete_targetservergroup (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  刪除指定的目標伺服器群組。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_delete_targetservergroup [ @name = ] 'name'   
```  
  
## <a name="arguments"></a>引數  
`[ @name = ] 'name'`要移除之目標伺服器群組的名稱。 *名稱*是**sysname**，沒有預設值。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功）或**1** （失敗）  
  
## <a name="result-sets"></a>結果集  
 None  
  
## <a name="permissions"></a>權限  
 需要**系統管理員（sysadmin** ）固定伺服器角色中的成員資格。  
  
## <a name="examples"></a>範例  
 下列範例會移除 `Servers Processing Customer Orders` 這個目標伺服器群組。  
  
```  
USE msdb ;  
GO  
  
EXEC sp_delete_targetservergroup  
    @name = N'Servers Processing Customer Orders';  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [sp_add_targetservergroup &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-add-targetservergroup-transact-sql.md)   
 [sp_help_targetservergroup &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-help-targetservergroup-transact-sql.md)   
 [sp_update_targetservergroup &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-update-targetservergroup-transact-sql.md)  
  
  
