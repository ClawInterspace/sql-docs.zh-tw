---
title: Item 屬性（ADO） |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Parameters::GetItem
- Indexes::GetItem
- Parameters::Item
- Tables::Item
- Procedures::Item
- Users::GetItem
- Tables::GetItem
- Procedures::GetItem
- Users::get_Item
- Users::Item
- Views::GetItem
- Groups::Item
- Groups::get_Item
- Columns::Item
- Indexes::Item
- Fields15::GetItem
- Columns::GetItem
- Fields::Item
- Indexes::get_Item
- Columns::get_Item
- Fields15::Item
- Views::get_Item
- Groups::GetItem
- Errors::get_Item
- Fields15::get_Item
- Tables::get_Item
- Views::Item
- Errors::GetItem
- Parameters::get_Item
- Errors::Item
- Procedures::get_Item
helpviewer_keywords:
- Item property [ADO]
ms.assetid: e11484bb-c5c7-42d8-9bb8-21572125d727
author: rothja
ms.author: jroth
ms.openlocfilehash: 2bc6cb28823a2b8faf79e4bf44fb405446e12514
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87242658"
---
# <a name="item-property-ado"></a>Item 屬性 (ADO)
以名稱或序數表示集合的特定成員。  
  
## <a name="syntax"></a>語法  
  
```  
Set object = collection.Item ( Index )  
```  
  
## <a name="return-value"></a>傳回值  
 傳回物件參考。  
  
## <a name="parameters"></a>參數  
 *Index*  
 會評估為名稱或集合中物件序號的**Variant**運算式。  
  
## <a name="remarks"></a>備註  
 使用**Item**屬性可傳回集合中的特定物件。 如果**專案**在對應至*索引*引數的集合中找不到物件，就會發生錯誤。 此外，某些集合不支援命名物件;對於這些集合，您必須使用序數參考。  
  
 **Item**屬性是所有集合的預設屬性;因此，下列語法形式可互換：  
  
```  
collection.Item (Index)  
collection (Index)  
```  
  
## <a name="applies-to"></a>套用至  

:::row:::
    :::column:::
        [Axes 集合 (ADO MD)](../../../ado/reference/ado-md-api/axes-collection-ado-md.md)  
        [Columns 集合 (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)  
        [CubeDefs 集合 (ADO MD)](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md)  
        [Dimensions 集合 (ADO MD)](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md)  
        [Errors 集合 (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)  
        [Fields 集合 (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)  
        [Groups 集合 (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)  
    :::column-end:::
    :::column:::
        [Hierarchies 集合 (ADO MD)](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)  
        [Indexes 集合 (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)  
        [Keys 集合 (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)  
        [Levels 集合 (ADO MD)](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)  
        [Members 集合 (ADO MD)](../../../ado/reference/ado-md-api/members-collection-ado-md.md)  
        [Parameters 集合 (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)  
    :::column-end:::
    :::column:::
        [Positions 集合 (ADO MD)](../../../ado/reference/ado-md-api/positions-collection-ado-md.md)  
        [Procedures 集合 (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)  
        [Properties 集合 (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)  
        [Tables 集合 (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)  
        [Users 集合 (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)  
        [Views 集合 (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>另請參閱  
 [Item 屬性範例（VB）](../../../ado/reference/ado-api/item-property-example-vb.md)   
 [Item 屬性範例 (VC++)](../../../ado/reference/ado-api/item-property-example-vc.md)   
