---
title: 靜態彙總幾何方法 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- Aggregate Geometry Methods [SQL Server]
ms.assetid: 4e19f582-ef8f-40f7-8ad1-4f08591cdd1a
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: f1ca6ee9fd45ee4e600dea5614c9421307a80477
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85748774"
---
# <a name="static-aggregate-geometry-methods"></a>靜態彙總幾何方法
[!INCLUDE [SQL Server Azure SQL Database ](../../includes/applies-to-version/sql-asdb.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支援下列彙總方法當做開放式地理空間協會 (Open Geospatial Consortium，OGC) 之靜態幾何方法的擴充。  
  
> [!NOTE]  
>  這些彙總方法只在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中公開。 它們不會在 Microsoft.SqlServer.Types 組件中公開。  
  
 如需有關 OGC 規格的詳細資訊，請參閱下列資源：  
  
 [OGC 規格，簡單特徵存取第一部 - 常見架構](https://go.microsoft.com/fwlink/?LinkId=93627)  
  
 [OGC 規格，簡單特徵存取第二部 - SQL 選項](https://go.microsoft.com/fwlink/?LinkId=93628) \(英文\)  
  
 [OGC 規格，地理標記語言](https://go.microsoft.com/fwlink/?LinkId=93629) \(英文\)  
  
## <a name="in-this-section"></a>本節內容  
  
-   [CollectionAggregate &#40;geometry 資料類型&#41;](../../t-sql/spatial-geometry/collectionaggregate-geometry-data-type.md)  
  
-   [ConvexHullAggregate &#40;geometry 資料類型&#41;](../../t-sql/spatial-geometry/convexhullaggregate-geometry-data-type.md)  
  
-   [EnvelopeAggregate &#40;geometry 資料類型&#41;](../../t-sql/spatial-geometry/envelopeaggregate-geometry-data-type.md)  
  
-   [UnionAggregate &#40;geometry 資料類型&#41;](../../t-sql/spatial-geometry/unionaggregate-geometry-data-type.md)  
  
## <a name="see-also"></a>另請參閱  
 [幾何執行個體上擴充的方法](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)   
 [擴充的靜態幾何方法](../../t-sql/spatial-geometry/extended-static-geometry-methods.md)   
 [幾何執行個體上的 OGC 方法](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)   
 [OGC 靜態幾何方法](../../t-sql/spatial-geometry/ogc-static-geometry-methods.md)  
  
  
