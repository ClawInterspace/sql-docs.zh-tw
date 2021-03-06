---
title: XQuery 語言參考（SQL Server） |Microsoft Docs
description: 瞭解用於 SQL Server 的 XQuery 語言，並查看完整的語言參考。
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
helpviewer_keywords:
- XQuery
- XQuery, about XQuery
- xml data type [SQL Server], XQuery
- XML [SQL Server], XQuery
- queries [XML in SQL Server], XQuery
ms.assetid: 8a69344f-2990-4357-8160-cb26aac95b91
author: rothja
ms.author: jroth
ms.openlocfilehash: a50ed63856e9998066db0b4d0791feb79478726c
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85734156"
---
# <a name="xquery-language-reference-sql-server"></a>Xquery 語言參考 (SQL Server)
[!INCLUDE [SQL Server Azure SQL Database ](../includes/applies-to-version/sqlserver.md)]

  [!INCLUDE[tsql](../includes/tsql-md.md)]支援用來查詢**xml**資料類型之 XQuery 語言的子集。 此 XQuery 實作是與 XQuery 的 July 2004 Working Draft 合作。 該語言是由 World Wide Web Consortium (W3C) 以及所有主要資料庫廠商，還有 Microsoft 聯合開發。 因為 W3C 規格可能會在成為 W3C 建議之前會歷經數次修改，所以此實行可能會跟最終的建議不同。 此主題說明 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 支援之 XQuery 子集的語意及語法。  
  
 如需詳細資訊，請參閱[W3C XQuery 1.0 語言規格](https://go.microsoft.com/fwlink/?LinkId=48846)。  
  
 XQuery 是可查詢結構化或半結構化 XML 資料的語言。 使用中提供的**xml**資料類型支援 [!INCLUDE[ssDE](../includes/ssde-md.md)] ，檔可儲存在資料庫中，然後使用 XQuery 進行查詢。  
  
 XQuery 是以現有的 XPath 查詢語言為基礎，加上額外支援以獲取更佳的反覆運算、更好的排序結果，以及建構必要 XML 的能力。 XQuery 可在 XQuery 資料模型上運作。 這是 XML 文件與已指定類型及不具類型之 XQuery 結果的摘要。 類型資訊是以 W3C XML 結構描述語言提供的類型為依據。 如果沒有類型資訊可用，XQuery 會將資料處理為不具類型。 這與 XPath 1.0 版處理 XML 的方式相似。  
  
 若要查詢儲存在**xml**類型之變數或資料行中的 xml 實例，您可以使用[Xml 資料類型方法](../t-sql/xml/xml-data-type-methods.md)。 例如，您可以宣告**xml**類型的變數，並使用**xml**資料類型的**query （）** 方法來查詢它。  
  
```sql
DECLARE @x xml  
SET @x = '<ROOT><a>111</a></ROOT>'  
SELECT @x.query('/ROOT/a')  
```  
  
 在下列範例中，查詢是針對 AdventureWorks 資料庫中 ProductModel 資料表內**xml**類型的 [指示] 資料行所指定。  
  
```sql
SELECT Instructions.query('declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";           
    /AWMI:root/AWMI:Location[@LocationID=10]  
') as Result   
FROM  Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 XQuery 包含命名空間宣告、 `declare namespace``AWMI=...` 和查詢運算式 `/AWMI:root/AWMI:Location[@LocationID=10]` 。  
  
 請注意，XQuery 是針對**xml**類型的 [指示] 資料行所指定。 Xml 資料類型的[query （）方法](../t-sql/xml/query-method-xml-data-type.md)是用來指定 XQuery。  
  
 下表中所列的相關主題可以協助您了解如何在 [!INCLUDE[ssDE](../includes/ssde-md.md)] 實作 XQuery。  
  
|主題|描述|  
|-----------|-----------------|  
|[XML 資料 &#40;SQL Server&#41;](../relational-databases/xml/xml-data-sql-server.md)|說明中**xml**資料類型的支援 [!INCLUDE[ssDE](../includes/ssde-md.md)] ，以及您可以針對此資料類型使用的方法。 **Xml**資料類型會形成執行 xquery 運算式所在的輸入 xquery 資料模型。|  
|[XML 結構描述集合 &#40;SQL Server&#41;](../relational-databases/xml/xml-schema-collections-sql-server.md)|描述如何指定資料庫中儲存之 XML 執行個體的類型。 這表示您可以將 XML 架構集合與**xml**類型資料行產生關聯。 資料行中儲存的所有執行個體，都是以集合中的結構描述進行驗證及指定類型，而且可為 XQuery 提供類型資訊。|  
|||  
  
> [!NOTE]  
>  本章節的組織是以 World Wide Web Consortium (W3C) XQuery Working Draft 規格為依據。 本章節中提供的部分圖表即採自上述規格。 本章節會比較 Microsoft XQuery 實作與 W3C 規格，描述 Microsoft XQuery 跟 W3C 的不同之處，以及指出不支援的 W3C 功能。 您可以從取得 W3C 規格 [http://www.w3.org/TR/2004/WD-xquery-20040723](https://go.microsoft.com/fwlink/?LinkId=48846) 。  
  
## <a name="in-this-section"></a>本節內容  
  
|主題|描述|  
|-----------|-----------------|  
|[XQuery 基本概念](../xquery/xquery-basics.md)|提供 XQuery 概念，還有運算式評估 (靜態及動態內容)、不可部分完成、有效布林值、XQuery 類型系統、比對順序類型，以及錯誤處理的基本概觀。|  
|[XQuery 運算式](../xquery/xquery-expressions.md)|描述 XQuery 主要運算式、路徑運算式、順序運算式、算術比較及邏輯運算式、XQuery 建構、FLWOR 運算式、條件式及量化運算式，以及順序類型的不同運算式。|  
|[模組和初構 &#40;XQuery&#41;](../xquery/modules-and-prologs-xquery.md)|描述 XQuery 初構。|  
|[針對 xml 資料類型的 XQuery 函數](../xquery/xquery-functions-against-the-xml-data-type.md)|描述可支援之 XQuery 函數的清單。|  
|[針對 xml 資料類型的 XQuery 運算子](../xquery/xquery-operators-against-the-xml-data-type.md)|描述可支援的 XQuery 運算式。|  
|[針對 xml 資料類型的其他範例 XQueries](../xquery/additional-sample-xqueries-against-the-xml-data-type.md)|提供其他 XQuery 範例。|  
  
## <a name="see-also"></a>另請參閱  
 [XML 資料 &#40;SQL Server&#41;](../relational-databases/xml/xml-data-sql-server.md)   
 [XML 結構描述集合 &#40;SQL Server&#41;](../relational-databases/xml/xml-schema-collections-sql-server.md)   
 [大量匯入與匯出 XML 文件的範例 &#40;SQL Server&#41;](../relational-databases/import-export/examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
  
  
