---
title: 什麼是存放集區？
titleSuffix: SQL Server big data clusters
description: 本文描述 SQL Server 2019 巨量資料叢集中的存放集區。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d7a9d3e9e16eb923e0954154b46362cdc88c0bff
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85730686"
---
# <a name="what-is-the-storage-pool-big-data-clusters-2019"></a>什麼是存放集區 ([!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)])？

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

本文說明 [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]中的「SQL Server 存放集區」  角色。 下列各節描述 SQL 存放集區的架構和功能。

## <a name="storage-pool-architecture"></a>存放集區架構

存放集區包含由 Linux 上的 SQL Server、Spark 和 HDFS 組成的存放裝置節點。 SQL 巨量資料叢集中的所有存放裝置節點都是 HDFS 叢集成員。

![存放集區架構](media/concept-storage-pool/scale-big-data-on-demand.png)

## <a name="responsibilities"></a>職責

存放裝置節點負責：

- 透過 Spark 的資料擷取。
- HDFS 中的資料儲存區 (Parquet 和分隔符號文字格式)。 HDFS 也提供資料持續性，因為 HDFS 資料會散佈到 SQL 巨量資料叢集中的所有存放裝置節點。
- 透過 HDFS 和 SQL Server 端點的資料存取。

## <a name="next-steps"></a>後續步驟

若要深入了解 [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]，請參閱下列資源：

- [什麼是 [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]？](big-data-cluster-overview.md)
- [工作坊：Microsoft [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]架構](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters) \(英文\)
