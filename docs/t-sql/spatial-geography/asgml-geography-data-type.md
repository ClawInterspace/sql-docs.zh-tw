---
title: AsGml (geography 資料型別) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- AsGml_(geography_Data_Type)_TSQL
- AsGml
- AsGml_TSQL
- AsGml (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- AsGml method
ms.assetid: 67795c64-d8d3-48dc-93ef-3c8a9274deb6
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: f6b4dc7090262a11d17239d8be50c72a637b04f3
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/21/2020
ms.locfileid: "86555524"
---
#  <a name="asgml---geography-data-type"></a>AsGml - geography 資料型別
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  傳回 **geography** 執行個體的地理標記語言 (GML) 表示法。  
  
 如需有關地理標記語言的詳細資訊，請參閱開放地理空間協會規格：[OGC 規格，地理標記語言](https://go.microsoft.com/fwlink/?LinkId=93629) \(英文\)。  
  
## <a name="syntax"></a>語法  
  
```  
  
.AsGml ( )  
```  

[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>傳回型別  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 傳回類型：**xml**  
  
 CLR 傳回類型：**SqlXml**  
  
## <a name="remarks"></a>備註  
  
## <a name="examples"></a>範例  
 下列範例會建立 `LineString` 例項，並使用 `AsGML()` 傳回此例項的 GML 描述。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.AsGml();  
```  
  
 這個方法會傳回 `LineString` 例項形式的描述。  
  
```  
<LineString xmlns="https://www.opengis.net/gml"><posList>47.656 -122.36 47.656 -122.343</posList></LineString>  
```  
  
## <a name="see-also"></a>另請參閱  
 [地理例項上擴充的方法](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
