---
title: sys.databases dm_pdw_os_performance_counters （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 0673a8f8-8bed-41eb-8959-a9e3e9e03a65
author: CarlRabeler
ms.author: carlrab
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 72164d23d8f2dbd27bb30f1341b288c96ab44cc0
ms.sourcegitcommit: df1f0f2dfb9452f16471e740273cd1478ff3100c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87396607"
---
# <a name="sysdm_pdw_os_performance_counters-transact-sql"></a>sys.databases dm_pdw_os_performance_counters （Transact-sql）
[!INCLUDE [pdw](../../includes/applies-to-version/pdw.md)]

  包含中節點之 Windows 效能計數器的相關資訊 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] 。  
  
|資料行名稱|資料類型|描述|範圍|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|包含計數器之節點的識別碼。<br /><br /> pdw_node_id 和 counter_name 形成此視圖的索引鍵。|請參閱[dm_pdw_nodes &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md)中的 node_id。|  
|counter_name|**nvarchar(255)**|Windows 效能計數器的名稱。||  
|counter_category|**nvarchar(255)**|Windows 效能計數器類別目錄的名稱。||  
|instance_name|**nvarchar(255)**|計數器的特定執行個體名稱。||  
|counter_value|**Decimal （38，10）**|計數器的目前值。||  
|last_update_time|**Datetime2 （3）**|上次更新值的時間戳記。||  
  
## <a name="see-also"></a>另請參閱  
 [SQL 資料倉儲和平行處理資料倉儲動態管理 Views &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
