---
title: sp_cursor （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cursor_TSQL
- sp_cursor
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cursor
ms.assetid: 41ade0ca-5f11-469d-bd4d-c8302ccd93b3
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a92b502368756fd86fc4facda7c0726260d88fea
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85869682"
---
# <a name="sp_cursor-transact-sql"></a>sp_cursor (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  要求定點更新。 這個程序會針對資料指標的提取緩衝區內的一個或多個資料列執行作業。 sp_cursor 的叫用方式是在表格式資料流程（TDS）封包中指定 ID = 1。  
  
||  
|-|  
|**適用**于： SQL Server （ [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 至[目前版本](https://go.microsoft.com/fwlink/p/?LinkId=299658)）。|  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_cursor  cursor, optype, rownum, table  
    [ , value[...n]]]  
```  
  
## <a name="arguments"></a>引數  
 *cursor*  
 資料指標控制代碼。 *cursor*是針對**int**輸入值呼叫的必要參數。 *cursor*是 SQL Server 所產生的*控制碼*值，由 sp_cursoropen 程式所傳回。  
  
 *optype*  
 這是必要參數，可指定資料指標將要執行哪一個作業。 *optype*需要下列其中一個**int**輸入值。  
  
|值|名稱|說明|  
|-----------|----------|-----------------|  
|0X0001|UPDATE|這是用來更新提取緩衝區內的一個或多個資料列。  *Rownum*中指定的資料列會重新存取和更新。|  
|0x0002|刪除|這是用來刪除提取緩衝區內的一個或多個資料列。 *Rownum*中指定的資料列會重新存取和刪除。|  
|0X0004|Insert|插入資料而不建立 SQL **INSERT**語句。|  
|0X0008|REFRESH|這是用來從基礎資料表重新填滿緩衝區，而且在更新或刪除因為開放式並行控制而失敗或者在 UPDATE 之後，可用來重新整理資料列。|  
|0X10|LOCK|導致在包含指定資料列的頁面上取得 SQL Server 的 U-鎖定。 這個鎖定與 S-Locks 相容，但是與 X-Locks 或其他 U-Locks 不相容。 可用來實作短期鎖定。|  
|0X20|SETPOSITION|只有在程式即將發出後續的 SQL Server 定位 DELETE 或 UPDATE 語句時，才會使用。|  
|0X40|ABSOLUTE|只能搭配 UPDATE 或 DELETE 使用。  ABSOLUTE 只能搭配 KEYSET 資料指標使用 (DYNAMIC 資料指標和 STATIC 資料指標則會忽略，而且無法更新)。<br /><br /> 注意：如果在尚未提取的索引鍵集中的資料列上指定了絕對值，此作業可能會導致平行存取檢查失敗，而且無法保證傳回結果。|  
  
 *rownum*  
 指定資料指標將要運作、更新或刪除提取緩衝區內的哪些資料列。  
  
> [!NOTE]  
>  這樣不會影響任何 RELATIVE、NEXT 或 PREVIOUS 提取作業的起點，也不會影響使用 sp_cursor 執行的任何更新或刪除。  
  
 *rownum*是針對**int**輸入值呼叫的必要參數。  
  
 1  
 代表提取緩衝區內的第一個資料列。  
  
 2  
 代表提取緩衝區內的第二個資料列。  
  
 3、4、5  
 代表第三個資料列，依此類推。  
  
 n  
 代表提取緩衝區內的第 n 個資料列。  
  
 0  
 代表提取緩衝區內的所有資料列。  
  
> [!NOTE]  
>  僅適用于 UPDATE、DELETE、REFRESH 或 LOCK *optype*值。  
  
 *table*  
 當資料指標定義牽涉到聯結或不明確的資料行名稱由*value*參數傳回時，用來識別*optype*適用之資料表的資料表名稱。 如果未指定特定的資料表，預設值為 FROM 子句內的第一個資料表。 *table*是需要字串輸入值的選擇性參數。 此字串可以指定為任何字元或 UNICODE 資料類型。 *資料表*可以是多部分資料表名稱。  
  
 *value*  
 用來插入或更新值。 *值*字串參數僅適用于 UPDATE 和 INSERT *optype*值。 此字串可以指定為任何字元或 UNICODE 資料類型。  
  
> [!NOTE]  
>  *值*的參數名稱可以由使用者指派。  
  
## <a name="return-code-values"></a>傳回碼值  
 使用 RPC 時，具有緩衝區編號0的定位刪除或更新作業，會針對提取緩衝區中的每個資料列傳回已完成的訊息，其*rowcount*為0（失敗）或1（成功）。  
  
## <a name="remarks"></a>備註  
  
## <a name="optype-parameter"></a>optype 參數  
 除了 SETPOSITION 與 UPDATE、DELETE、REFRESH 或 LOCK 的組合之外，或者，如果是 UPDATE 或 DELETE，則*optype*值是互斥的。  
  
 UPDATE 值的 SET 子句是從*value*參數所構成。  
  
 使用 INSERT *optype*值的其中一個優點是，您可以避免將非字元資料轉換成字元格式以進行插入。 這些值的指定方式與 UPDATE 相同。 如果未包含任何必要的資料行，INSERT 將會失敗。  
  
-   SETPOSITION 值不會影響任何 RELATIVE、NEXT 或 PREVIOUS 提取作業的起點，也不會影響使用 sp_cursor 介面執行的任何更新或刪除。 未在提取緩衝區內指定資料列的任何數字將會導致位置設定為 1，而且不會傳回任何錯誤。 一旦執行 SETPOSITION，位置會持續生效，直到下一個 sp_cursorfetch 作業、T-sql **FETCH**作業，或透過相同的資料指標 sp_cursor SETPOSITION 作業為止。 後續的 sp_cursorfetch 作業會將資料指標的位置設定為新提取緩衝區內的第一個資料列，而其他資料指標呼叫將不會影響該位置的值。 SETPOSITION 可以透過 OR 子句來連結 REFRESH、UPDATE、DELETE 或 LOCK，以便將該位置的值設定為上一個修改的資料列。  
  
 如果未透過*rownum*參數指定提取緩衝區中的資料列，則位置會設定為1，而且不會傳回任何錯誤。 一旦設定位置之後，該位置就會生效，一直到透過相同資料指標執行下一個 sp_cursorfetch 作業、T-SQL FETCH 作業或 sp_cursor SETPOSITION 作業為止。  
  
 SETPOSITION 可以透過 OR 子句來連結 REFRESH、UPDATE、DELETE 或 LOCK，以便將資料指標位置設定為上一個修改的資料列。  
  
## <a name="rownum-parameter"></a>rownum 參數  
 如果指定， *rownum*參數可以解讀為索引鍵集內的資料列編號，而不是提取緩衝區內的資料列編號。 使用者負責確認並行控制的維護。 這表示對於 SCROLL_LOCKS 資料指標而言，您必須獨立維護給定資料列的鎖定 (可以透過交易來完成)。 對於 OPTIMISTIC 資料指標而言，您之前必須已經提取資料列，才能執行這項作業。  
  
## <a name="table-parameter"></a>table 參數  
 如果*optype*值是 UPDATE 或 insert，而且完整的 UPDATE 或 insert 語句是以*value*參數的形式提交，則會忽略為*table*指定的值。  
  
> [!NOTE]  
>  與檢視表有關，只能修改參與檢視表的一個資料表。 *值*參數資料行名稱必須反映視圖中的資料行名稱，但資料表名稱可以是基礎基表的名稱（在此情況下，sp_cursor 會取代視圖名稱）。  
  
## <a name="value-parameter"></a>value 參數  
 如先前在引數一節中所述，使用*值*的規則有兩個替代方案：  
  
1.  您可以針對任何已命名的值參數，使用已預先暫止的名稱，做 \@ 為選取清單中的資料行*value*名稱。 這個替代方案的一個優點是可能不需要轉換資料。  
  
2.  請使用參數來提交完整的 UPDATE 或 INSERT 語句，或是使用多個參數來提交 UPDATE 或 INSERT 語句的部分，SQL Server 將會建立到完整的語句中。 這部分的範例可以在本主題稍後的＜範例＞一節找到。  
  
## <a name="examples"></a>範例  
  
### <a name="alternative-value-parameter-uses"></a>其他值參數的使用  
 如果是 UPDATE：  
  
 當使用單一參數時，可以使用下列語法來提交 UPDATE 陳述式：  
  
 `[ [ UPDATE <table name> ] SET ] {<column name> = expression} [,...n]`  
  
> [!NOTE]  
>  如果 \<table name> 已指定 UPDATE，則會忽略為*table*參數指定的任何值。  
  
 當使用多個參數時，第一個參數必須是以下格式的字串：  
  
 `[ SET ] <column name> = expression  [,...n]`  
  
 後續的參數必須是以下的格式：  
  
 `<column name> = expression  [,...n]`  
  
 在此情況下， \<table name> 結構化 update 語句中的是由*table*參數指定或預設為的。  
  
 如果是 INSERT：  
  
 當使用單一參數時，可以使用下列語法來提交 INSERT 陳述式：  
  
 `[ [ INSERT [INTO] <table name> ] VALUES ] ( <expression> [,...n] )`  
  
> [!NOTE]  
>  如果 *\<table name>* 指定 INSERT，將會忽略為*table*參數指定的任何值。  
  
 當使用多個參數時，第一個參數必須是以下格式的字串：  
  
 `[ VALUES ( ] <expression>  [,...n]`  
  
 後續的參數必須是以下的格式：  
  
 `expression [,...n]`  
  
 除非在指定 VALUES 的情況下，此時最後一個運算式後面必須有尾端 ")"。 在此情況下， *\<table name>* 結構化 UPDATE 語句中的是由*table*參數指定或預設為的。  
  
> [!NOTE]  
>  可以將一個參數當做具名參數來提交，也就是 "`@VALUES`"。 在此情況下，無法使用其他具名參數。  
  
## <a name="see-also"></a>另請參閱  
 [sp_cursoropen &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-cursoropen-transact-sql.md)   
 [sp_cursorfetch &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-cursorfetch-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
