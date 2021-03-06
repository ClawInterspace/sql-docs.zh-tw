---
title: sys.databases dm_db_xtp_index_stats （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 08/29/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_db_xtp_index_stats
- dm_db_xtp_index_stats
- sys.dm_db_xtp_index_stats_TSQL
- dm_db_xtp_index_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_xtp_index_stats dynamic management view
ms.assetid: 8d0a50b8-2015-4576-930f-e3307dfc888e
author: CarlRabeler
ms.author: carlrab
monikerRange: =azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 91afcf9bc654c73b6dad416bf9c5d114ca1edee5
ms.sourcegitcommit: 039fb38c583019b3fd06894160568387a19ba04e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2020
ms.locfileid: "87442691"
---
# <a name="sysdm_db_xtp_index_stats-transact-sql"></a>sys.dm_db_xtp_index_stats (Transact-SQL)
[!INCLUDE[sql-asdb-asdbmi](../../includes/applies-to-version/sql-asdb-asdbmi.md)]

  包含上次重新啟動資料庫之後收集的統計資料。  
  
 如需詳細資訊，請參閱記憶體內部[&#40;記憶體優化&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)和在[記憶體優化資料表上使用索引的指導方針](https://msdn.microsoft.com/library/16ef63a4-367a-46ac-917d-9eebc81ab29b)。  

  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|object_id|**bigint**|這個索引所屬物件的識別碼。|  
|xtp_object_id|**bigint**|對應至目前物件版本的內部識別碼。<br /><br /> 注意：適用于 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 。|  
|index_id|**bigint**|索引的識別碼。 index_id 只在物件內才是唯一的。|  
|scans_started|**bigint**|已執行之記憶體中 OLTP 索引掃描的數目。 每個選取、插入、更新或刪除都需要索引掃描。|  
|scans_retries|**bigint**|必須重試的索引掃描數目。|  
|rows_returned|**bigint**|建立資料表或啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之後傳回的資料列累計數目。|  
|rows_touched|**bigint**|建立資料表或啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之後存取的資料列累計數目。|  
|rows_expiring|**bigint**|僅供內部使用。|  
|rows_expired|**bigint**|僅供內部使用。|  
|rows_expired_removed|**bigint**|僅供內部使用。|  
|phantom_scans_started|**bigint**|僅供內部使用。|  
|phatom_scans_retries|**bigint**|僅供內部使用。|  
|phantom_rows_touched|**bigint**|僅供內部使用。|  
|phantom_expiring_rows_encountered|**bigint**|僅供內部使用。|  
|phantom_expired_rows_encountered|**bigint**|僅供內部使用。|  
|phantom_expired_removed_rows_encountered|**bigint**|僅供內部使用。|  
|phantom_expired_rows_removed|**bigint**|僅供內部使用。|  
|object_address|**varbinary(8)**|僅供內部使用。|  
  
## <a name="permissions"></a>權限  
 需要目前資料庫的 VIEW DATABASE STATE 權限。  
  
## <a name="see-also"></a>另請參閱  
 [記憶體最佳化的資料表動態管理檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  
