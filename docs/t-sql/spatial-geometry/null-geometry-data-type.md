---
title: Null (geometry 資料類型) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Null (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- Null (geometry Data Type)
ms.assetid: 67a4b019-9091-4443-85cc-f4836d0cb509
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 9e93cb4a8e079d54098ff0a7c466de0227965487
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/21/2020
ms.locfileid: "86555095"
---
# <a name="null-geometry-data-type"></a>Null (geometry 資料類型)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

這是提供 **geometry** 類型之 Null 執行個體的唯讀屬性。
  
## <a name="syntax"></a>語法  
  
```  
  
Null  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>引數
  
## <a name="return-types"></a>傳回型別  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 類型：**geometry**  
  
 CLR 類型：**SqlGeometry**  
  
## <a name="remarks"></a>備註  
  
## <a name="examples"></a>範例  
 下列範例會擷取 Null `geometry`執行個體。  
  
```  
DECLARE @g geometry;   
SET @g = geometry::[Null];  
SELECT @g  
```  
  
## <a name="see-also"></a>另請參閱  
 [擴充的靜態幾何方法](../../t-sql/spatial-geometry/extended-static-geometry-methods.md)  
  
  

