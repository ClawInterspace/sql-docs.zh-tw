---
title: MinDbCompatibilityLevel (geometry 資料型別) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- MinDbCompatibilityLevel method (geometry)
ms.assetid: c848b974-8ccb-4c5c-a7eb-b019a9538d99
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 373c9eb4a1482bf92ae41c39af2f8852d19aac9f
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/21/2020
ms.locfileid: "86554337"
---
# <a name="mindbcompatibilitylevel-geometry-data-type"></a>MinDbCompatibilityLevel (geometry 資料類型)
[!INCLUDE [SQL Server Azure SQL Database ](../../includes/applies-to-version/sql-asdb.md)]

傳回可辨識 **geometry** 資料型別執行個體的最低資料庫相容性層級。
  
## <a name="syntax"></a>語法  
  
```  
  
.MinDbCompatibilityLevel ( )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>傳回型別
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 傳回類型：**int**  
  
 CLR 傳回類型：**int**  
  
## <a name="remarks"></a>備註  
 在變更資料庫的相容性層級之前，請先使用 `MinDbCompatibilityLevel()` 測試空間物件的相容性。  
  
## <a name="examples"></a>範例  
  
### <a name="a-testing-circularstring-type-for-compatibility-with-compatibility-level-110"></a>A. 使用相容性層級 110 測試 CircularString 類型的相容性  
 下列範例會測試 `CircularString` 執行個體與舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的相容性：  
  
```
 DECLARE @g geometry = 'CIRCULARSTRING(3 4, 8 9, 5 6)'; 
 IF @g.MinDbCompatibilityLevel() <= 110 
 BEGIN 
 SELECT @g.ToString(); 
 END
 ```  
  
### <a name="b-testing-linestring-type-for-compatibility-with-compatibility-level-100"></a>B. 使用相容性層級 100 測試 LineString 類型的相容性  
 下列範例會測試 `LineString` 執行個體與 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 的相容性：  
  
```
 DECLARE @g geometry = 'LINESTRING(3 4, 8 9, 5 6)'; 
 IF @g.MinDbCompatibilityLevel() <= 100 
 BEGIN 
 SELECT @g.ToString(); 
 END
``` 
  
## <a name="see-also"></a>另請參閱  
 [ALTER DATABASE 相容性層級 &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)  
  
  

