---
title: PredictCaseLikelihood （DMX） |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 3c1134e5cf1ca053cba52c943226f41fe3d4b625
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "86971547"
---
# <a name="predictcaselikelihood-dmx"></a>PredictCaseLikelihood (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  這個函數會傳回輸入案例符合現有模型的可能性。 只適用於群集模型。  
  
## <a name="syntax"></a>語法  
  
```  
  
PredictCaseLikelihood([NORMALIZED|NONNORMALIZED])  
```  
  
## <a name="arguments"></a>引數  
 NORMALIZED  
 傳回值包含模型內案例的機率除以無模型案例的機率。  
  
 NONNORMALIZED  
 傳回值包含案例的原始機率，也就是案例屬性機率的乘積。  
  
## <a name="applies-to"></a>套用至  
 使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] 群集與時序群集演算法建立的模型 [!INCLUDE[msCoName](../includes/msconame-md.md)] 。  
  
## <a name="return-type"></a>傳回類型  
 介於 0 和 1 之間的雙精確度浮點數。 較接近 1 的數字代表案例在此模型中發生的機率較高。 較接近 0 的數字代表案例較不可能在此模型中發生。  
  
## <a name="remarks"></a>備註  
 根據預設， **PredictCaseLikelihood**函數的結果是正規化的。 隨著案例中的屬性數增加，而任兩個案例之間的原始機率差異更小時，正規化的值通常會變得更有用。  
  
 下列方程式是在 x 和 y 已知時，用來計算正規化的值：  
  
-   x = 以群集模型為基礎的案例可能性  
  
-   y = 臨界案例可能性，根據計算培訓案例而計算為案例的對數可能性  
  
-   Z = Exp （記錄（x）-記錄（Y））  
  
 正規化 = （z/（1 + z））  
  
## <a name="examples"></a>範例  
 下列範例根據 [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW 資料庫，傳回指定的案例在叢集模型內出現的可能性。  
  
```  
SELECT  
  PredictCaseLikelihood() AS Default_Likelihood,  
  PredictCaseLikelihood(NORMALIZED) AS Normalized_Likelihood,  
  PredictCaseLikelihood(NONNORMALIZED) AS Raw_Likelihood,  
FROM  
  [TM Clustering]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
 預期的結果：  
  
|Default_Likelihood|Normalized_Likelihood|Raw_Likelihood|  
|-------------------------|----------------------------|---------------------|  
|6.30672792729321E-08|6.30672792729321E-08|9.5824454056846E-48|  
  
 這些結果之間的差異示範了正規化的效果。 **CaseLikelihood**的原始值會建議案例的機率約為 20%;不過，當您將結果正規化時，案例的可能性會明顯降低。  
  
## <a name="see-also"></a>另請參閱  
 [資料採礦演算法 &#40;Analysis Services-資料採礦&#41;](https://docs.microsoft.com/analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining)   
 [資料採礦延伸模組 &#40;DMX&#41; 函數參考](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [DMX&#41;的函數 &#40;](../dmx/functions-dmx.md)   
 [&#40;DMX&#41;的一般預測函數](../dmx/general-prediction-functions-dmx.md)  
  
  
