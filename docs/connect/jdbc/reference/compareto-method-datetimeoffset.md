---
title: compareTo 方法 (DateTimeOffset) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e4cf2ea4-0fe9-40ce-ba79-f2a2b616997e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ac80b43813106f1de991da5114b2473871222a68
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2020
ms.locfileid: "80923572"
---
# <a name="compareto-method-datetimeoffset"></a>compareTo 方法 (DateTimeOffset)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  將此 **DateTimeOffset** 物件與另一個 **DateTimeOffset** 物件比較，並以 GMT 的時間為基礎。  
  
## <a name="syntax"></a>語法  
  
```  
  
public int compareTo(DateTimeOffset other)  
```  
  
#### <a name="parameters"></a>參數  
 您想要與目前執行個體比較的 [DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) 值。  
  
## <a name="return-value"></a>傳回值  
 下表描述此方法的傳回值。  
  
|傳回值|描述|  
|------------------|-----------------|  
|0|兩個 **DateTimeOffset** 物件都代表相同的時間點。|  
|負數|此 **DateTimeOffset** 物件代表比*其他*物件要早的時間點。|  
|正數|此 **DateTimeOffset** 物件代表比*其他*物件要晚的時間點。|  
  
## <a name="remarks"></a>備註  
 當兩個 **DateTimeOffset** 物件有相同的 GMT 時間時，根據位移，物件就沒有其他順序。  
  
## <a name="see-also"></a>另請參閱  
 [DateTimeOffset 類別](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [DateTimeOffset 成員](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
