---
title: catalog.startup | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 271fd405-246a-4852-bfbe-f557241ce6ea
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fedf6c41eb47de9fdafef5375af7f0f04b0ab335
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "86912757"
---
# <a name="catalogstartup"></a>catalog.startup 

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  執行 SSISDB 目錄之作業狀態的維護。  
  
 預存程序會在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 伺服器執行個體效能降低時，修正正在執行之任何封裝的狀態。  
  
 您可以選擇讓預存程序在每次 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 伺服器執行個體重新啟動時自動執行，方法是選取 [建立目錄] 對話方塊中的 [在 SQL Server 啟動時允許自動執行 Integration Services 預存程序] 選項。  
  
## <a name="syntax"></a>語法  
  
```sql  
catalog.startup  
```  
  
## <a name="return-code-value"></a>傳回碼值  
 0 (成功)  
  
## <a name="result-sets"></a>結果集  
 None  
  
## <a name="permissions"></a>權限  
 這個預存程序需要下列其中一個權限：  
  
-   執行執行個體的 READ 和 MODIFY 權限、專案的 READ 和 EXECUTE 權限，以及 (如果適用的話) 參考環境的 READ 權限  
  
-   **ssis_admin** 資料庫角色的成員資格  
  
-   **系統管理員**伺服器角色的成員資格  
  
  
