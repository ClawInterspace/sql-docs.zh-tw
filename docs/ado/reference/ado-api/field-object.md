---
title: Field 物件 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field
helpviewer_keywords:
- Field object [ADO]
ms.assetid: b10a72fc-3c4b-4186-a70b-993dc9f7a092
author: rothja
ms.author: jroth
ms.openlocfilehash: 8a50d9f3354f9d5eb5a7615c244d8a8990ffc0c9
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2020
ms.locfileid: "82758764"
---
# <a name="field-object"></a>Field 物件
表示具有 common 資料類型的資料行。  
  
## <a name="remarks"></a>備註  
 每個**Field**物件都會對應至[記錄集](../../../ado/reference/ado-api/recordset-object-ado.md)內的資料行。 您可以使用**欄位**物件的[Value](../../../ado/reference/ado-api/value-property-ado.md)屬性來設定或傳回目前記錄的資料。 視提供者公開的功能而定，可能無法使用**欄位**物件的某些集合、方法或屬性。  
  
 使用**Field**物件的集合、方法和屬性，您可以執行下列動作：  
  
-   傳回具有[name](../../../ado/reference/ado-api/name-property-ado.md)屬性之欄位的名稱。  
  
-   使用**Value**屬性來查看或變更欄位中的資料。 **Value**是**Field**物件的預設屬性。  
  
-   傳回具有[類型](../../../ado/reference/ado-api/type-property-ado.md)、有效[位數](../../../ado/reference/ado-api/precision-property-ado.md)和[NumericScale](../../../ado/reference/ado-api/numericscale-property-ado.md)屬性之欄位的基本特性。  
  
-   傳回具有[DefinedSize](../../../ado/reference/ado-api/definedsize-property.md)屬性之欄位的宣告大小。  
  
-   使用[ActualSize](../../../ado/reference/ado-api/actualsize-property-ado.md)屬性傳回給定欄位中的資料實際大小。  
  
-   使用[屬性](../../../ado/reference/ado-api/attributes-property-ado.md)（attribute [）屬性（attribute）集合，](../../../ado/reference/ado-api/properties-collection-ado.md)判斷指定欄位支援的功能類型。  
  
-   使用[AppendChunk](../../../ado/reference/ado-api/appendchunk-method-ado.md)和[GetChunk](../../../ado/reference/ado-api/getchunk-method-ado.md)方法操作包含長二進位或長字元資料的欄位值。  
  
-   如果提供者支援批次更新，請使用[OriginalValue](../../../ado/reference/ado-api/originalvalue-property-ado.md)和[UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md)屬性，在批次更新期間解決域值不一致的情況。  
  
 在開啟**欄位**物件的**記錄集**之前，所有的中繼資料屬性（**Name**、 **Type**、 **DefinedSize**、 **Precision**和**NumericScale**）都可供使用。 在這段時間進行設定，適用于動態地建立表單。  
  
 本章節包含下列主題。  
  
-   [Field 物件屬性、方法和事件](../../../ado/reference/ado-api/field-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>另請參閱  
 [Fields 集合（ADO）](../../../ado/reference/ado-api/fields-collection-ado.md)   
 [Properties 集合（ADO）](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Recordset 物件 (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
