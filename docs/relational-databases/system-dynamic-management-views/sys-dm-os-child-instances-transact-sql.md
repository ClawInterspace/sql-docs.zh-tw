---
title: sys.databases dm_os_child_instances （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_child_instances
- sys.dm_os_child_instances_TSQL
- dm_os_child_instances
- dm_os_child_instances_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- server state information [SQL Server]
- sys.dm_os_child_instances dynamic management view
- monitoring server health
ms.assetid: 1bef3074-0ccc-48fa-8f3d-14f3d99df86b
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 58830fc28bea6432e32629c43c103f2ba9cd7ad5
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85898799"
---
# <a name="sysdm_os_child_instances-transact-sql"></a>sys.dm_os_child_instances (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  針對已經從父伺服器執行個體建立的每個使用者執行個體，各傳回一個資料列。  
  
> **重要！** [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 從**dm_os_child_instances sys.databases**傳回的資訊可以用來判斷每個使用者實例的狀態（heart_beat），並取得可用來建立使用或 SQLCmd 之使用者實例連接的管道名稱（instance_pipe_name） [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 。 您只能連接到已由外部處理序 (例如，用戶端應用程式) 啟動的使用者執行個體。 SQL 管理工具無法啟動使用者執行個體。  
  
> **注意：** 使用者實例僅為的一項功能 [!INCLUDE[ssExpressEd11](../../includes/ssexpressed11-md.md)] 。  
> 
> **注意**若要從或呼叫此 [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] ，請使用**dm_pdw_nodes_os_child_instances**的名稱。  
  
|資料行|資料類型|描述|  
|------------|---------------|-----------------|  
|**owning_principal_name**|**nvarchar(256)**|建立這個使用者執行個體的使用者名稱。|  
|owning_principal_sid|nvarchar(256)|擁有這個使用者執行個體之主體的 SID (安全性識別碼)。 這個識別碼與 Windows SID 相符。|  
|owning_principal_sid_binary|varbinary(85)|擁有使用者執行個體之使用者的 SID 二進位版本|  
|**instance_name**|**nvarchar(128)**|這個使用者執行個體的名稱。|  
|**instance_pipe_name**|**nvarchar(260)**|在建立使用者執行個體時，系統會針對要連接的應用程式建立具名管道。 這個名稱可用於連接字串，以連接這個使用者執行個體。|  
|**os_process_id**|**整數**|這個使用者執行個體的 Windows 處理序號碼。|  
|**os_process_creation_date**|**從中**|上次啟動這個使用者執行個體的日期和時間。|  
|**heart_beat**|**Nvarchar （5）**|這個使用者執行個體目前的狀態，可能為 ALIVE 或 DEAD。|  
|**pdw_node_id**|**int**|**適用**于： [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] 、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> 此散發所在節點的識別碼。|  
  
## <a name="permissions"></a>權限  
 需要伺服器的 VIEW SERVER STATE 權限。  
  
## <a name="remarks"></a>備註  
 如需動態管理檢視的詳細資訊，請參閱《線上叢書》中的[動態管理 Views 和函數 &#40;transact-sql&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。  
  
## <a name="see-also"></a>另請參閱  
 [非管理員的使用者執行個體](https://msdn.microsoft.com/85385aae-10fb-4f8b-9eeb-cce2ee7da019)  
  
  



