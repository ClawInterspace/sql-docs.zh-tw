---
title: 使用 Data Migration Assistant 建立 SSIS 遷移評量
description: 瞭解如何使用 Data Migration Assistant 來評估內部部署 SQL Server 整合服務 (SSIS) ，再遷移至 Azure SQL Database 或 Azure SQL 受控執行個體
ms.date: 08/23/2019
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Assess
ms.assetid: ''
author: chugugrace
ms.author: chugu
ms.custom: seo-lt-2019
ms.openlocfilehash: 9a7b077c3046b2f0c7e50b7ec20f68a5544e91e1
ms.sourcegitcommit: 777704aefa7e574f4b7d62ad2a4c1b10ca1731ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2020
ms.locfileid: "87822193"
---
# <a name="perform-a-sql-server-integration-service-migration-assessment-with-data-migration-assistant"></a>使用 Data Migration Assistant 執行 SQL Server 整合服務遷移評估

## <a name="prerequisites"></a>必要條件

若要評估 SQL Server 整合服務 (SSIS) 套件，下列元件必須與 Data Migration Assistant 一起安裝：

- 與要評估的 SSIS 封裝版本相同的 SQL Server 整合服務。
- Azure Feature Pack 或其他協力廠商元件（如果要評估的 SSIS 封裝具有這些元件）。  

DMA 必須以**系統管理員**存取權執行，才能評估封裝存放區中的 SSIS 套件。

## <a name="performance-assessments"></a>效能評定

下列逐步指示可協助您執行第一個評估，以使用受控執行個體將 SQL Server 整合服務 (SSIS) 套件遷移至 Azure SQL Database 或 Azure SQL Data Migration Assistant。

## <a name="create-an-assessment"></a>建立評估

1. 選取 [**新增** (+) ] 圖示，然後選取 [**評估**] 專案類型為 [**整合服務**]。

1. 設定來源和目標伺服器類型。

    選取 [來源] 做為 [ **SQL Server**]，然後將 [目標伺服器類型] 設定為**AZURE SQL DATABASE**或**Azure SQL 受控執行個體**。

1. 按一下 [建立]。

    ![建立評量](media/dma-assess-ssis/dma-assess-ssis-create.png)

## <a name="connect-to-a-server"></a>連接到伺服器

1. 遵循預設選項，然後按 **[下一步] [** **選取來源**]。
1. 輸入 SQL server 實例名稱，選擇 [驗證類型]，並設定正確的連接屬性。
1.  (選擇性) 輸入包含 SSIS 封裝的資料夾路徑。
1.  (選擇性) 輸入套件加密密碼（如果適用）。
1. 按一下 [連接到來源 SQL server **]** 。
  ![新增來源](media/dma-assess-ssis/dma-assess-ssis-addsource.png)

## <a name="add-sources-to-assess"></a>新增要評估的來源

1. 選取要評估的 SSIS 套件儲存類型，然後選取 [**新增**]。
![新增來源](media/dma-assess-ssis/dma-assess-ssis-addsource-type.png)
1. 如果需要評估多個資料夾，請選取 [**新增來源**] 以開啟 [連線] 飛出視窗功能表。
1. 按一下 [開始評估]****。
  ![開始評估](media/dma-assess-ssis/dma-assess-ssis-assess.png)

## <a name="view-results"></a>檢視結果

相容性問題類別提供部分支援或不支援的功能，會封鎖將內部部署 SSIS 套件遷移至 Azure SSIS Integration Runtime。 接著，它會提供可協助您解決這些問題的建議。

![檢視結果](media/dma-assess-ssis/dma-assess-ssis-result.png)

## <a name="next-steps"></a>後續步驟

- [將內部部署 SSIS 工作負載遷移至 ADF 中的 SSIS 總覽](https://docs.microsoft.com/azure/data-factory/scenario-ssis-migration-overview)
- [將 SQL Server Integration Services 套件遷移至 Azure SQL 受控執行個體](https://docs.microsoft.com/azure/dms/how-to-migrate-ssis-packages-managed-instance)
- [將 SQL Server Integration Services 封裝重新部署至 Azure SQL Database](https://docs.microsoft.com/azure/dms/how-to-migrate-ssis-packages)
