---
title: 建立 Master Data Services 資料庫
description: 當您需要新的資料庫來支援主資料管理員 web 應用程式和 Master Data Services web 服務時，請建立 Master Data Services 資料庫。
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 8373bb35-f0f9-4c3c-a53c-dfaa2ce567ac
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: af13d59ddb5c8837959feb83b31fc17dbcd7aa29
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85883872"
---
# <a name="create-a-master-data-services-database"></a>建立 Master Data Services 資料庫

[!INCLUDE [SQL Server Windows Only - ASDBMI ](../../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  當您需要新的資料庫支援 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Web 應用程式及 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 服務時，請建立 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 資料庫。  
  
## <a name="prerequisites"></a>必要條件  
  
-   如需主控資料庫之電腦需求的相關資訊，請參閱[資料庫需求 &#40;Master Data Services&#41;](../../master-data-services/install-windows/database-requirements-master-data-services.md)。  
  
### <a name="to-create-a-master-data-services-database"></a>若要建立 Master Data Services 資料庫  
  
1.  開啟 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]。  
  
2.  按一下左窗格中的 [資料庫組態]****。  
  
3.  在 [資料庫組態]**** 頁面上，按一下 [建立資料庫]****。  
  
4.  完成 [建立資料庫]**** 精靈，建立及設定此資料庫。 如需精靈中之使用者介面 (UI) 選項的相關資訊，請參閱 [Create Database Wizard &#40;Master Data Services Configuration Manager&#41;](../../master-data-services/create-database-wizard-master-data-services-configuration-manager.md) (建立資料庫精靈 (Master Data Services 組態管理員))。  
  
## <a name="next-steps"></a>後續步驟  
  
-   設定資料庫及 Web 應用程式的系統設定。 如需詳細資訊，請參閱 [系統設定 &#40;Master Data Services&#41;](../../master-data-services/system-settings-master-data-services.md)。  
  
-   建立要關聯到此資料庫的 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 應用程式。 如需詳細資訊，請參閱[建立主資料管理員 Web 應用程式 &#40;Master Data Services&#41;](../../master-data-services/install-windows/create-a-master-data-manager-web-application-master-data-services.md)。  
  
-   設定維護計畫來備份資料庫和交易記錄。 如需詳細資訊，請參閱[資料庫需求 &#40;Master Data Services&#41;](../../master-data-services/install-windows/database-requirements-master-data-services.md)。  
  
## <a name="see-also"></a>另請參閱  
 [安裝 Master Data Services](../../master-data-services/install-windows/install-master-data-services.md)  
  
  
