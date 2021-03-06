---
title: ClusterProbability （DMX） |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 60c95521ba42dc5877c0e10a3f34453a497ad438
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "86969933"
---
# <a name="clusterprobability-dmx"></a>ClusterProbability (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  傳回輸入案例屬於指定之群集的機率。  
  
## <a name="syntax"></a>Syntax  
  
```  
  
ClusterProbability([<Node_Caption>])  
```  
  
## <a name="applies-to"></a>套用至  
 唯有基礎資料採礦模型支援群集時，才能使用這個函數。  
  
## <a name="return-type"></a>傳回類型  
 純量值。  
  
## <a name="remarks"></a>備註  
 下列語法使用採礦模型內容結構描述資料列集，傳回採礦模型中存在的節點標題。  
  
```  
SELECT NODE_CAPTION FROM <model>.CONTENT  
```  
  
 如需使用此語法的詳細資訊，請參閱[SELECT FROM &#60;model&#62;。DMX&#41;的內容 &#40;](../dmx/select-from-model-content-dmx.md)。 如需有關「採礦模型內容架構資料列集」的詳細資訊，請參閱 DMSCHEMA_MINING_MODEL_CONTENT 資料列[集](https://docs.microsoft.com/previous-versions/sql/sql-server-2012/ms126267(v=sql.110))。  
  
 如果 \<node caption> 未指定，此函數會傳回輸入案例屬於最可能之群集的機率。 使用**cluster**函數來傳回最可能的叢集。  
  
## <a name="examples"></a>範例  
 下列範例傳回指定的案例存在標示為 Cluster 2 之叢集內的機率。  
  
```  
SELECT  
  ClusterProbability('Cluster 2')  
From  
  [TM Clustering]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
## <a name="see-also"></a>另請參閱  
 [&#40;DMX&#41;的叢集](../dmx/cluster-dmx.md)   
 [資料採礦延伸模組 &#40;DMX&#41; 函數參考](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [DMX&#41;的函數 &#40;](../dmx/functions-dmx.md)   
 [&#40;DMX&#41;的一般預測函數](../dmx/general-prediction-functions-dmx.md)  
  
  
