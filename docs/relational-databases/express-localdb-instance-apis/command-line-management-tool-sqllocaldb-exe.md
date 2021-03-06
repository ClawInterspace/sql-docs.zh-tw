---
title: 命令列管理工具： SqlLocalDB.exe |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
apilocation:
- sqluserinstance.dll
ms.assetid: dd0882b1-a8a9-447a-8bdf-0f9d7f36d336
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5c39272a1f8af7fce092f7aa31ac3a4f7ebd2263
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85765250"
---
# <a name="command-line-management-tool-sqllocaldbexe"></a>命令列管理工具：SqlLocalDB.exe
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  SqlLocalDB.exe 是可讓使用者從命令列輕鬆管理 LocalDB 執行個體的簡單工具。 它會實作為 LocalDB 執行個體 API 外圍的簡單包裝函式。 就像在許多類似的 SQL Server 工具 (例如 SQLCMD) 中一樣，參數會當做命令列引數傳遞給 SqlLocalDB，並且將輸出傳送到主控台。  
  
 SqlLocalDB 可讓開發人員使用 LocalDB，而不需要撰寫呼叫 API 的程式碼，或依賴其他工具來完成作業。  
  
## <a name="sqllocaldb-options"></a>SqlLocalDB 選項  
 SqlLocalDB 支援下列選項。  
  
|選項|作用|  
|------------|------------------|  
|`-?`|列印說明文字。|  
|`create\|c "instance name" [version-number] [-s]`|以指定的名稱和版本建立新的 LocalDB 執行個體。<br /><br /> 如果省略 [version-number] 參數，預設為 SqlLocalDB 組建版本。<br /><br /> -s 會啟動新建立的 LocalDB 執行個體。|  
|`delete\|d "instance name"`|刪除具有指定之名稱的 LocalDB 執行個體。|  
|`start\|s "instance name"`|啟動具有指定之名稱的 LocalDB 執行個體。|  
|`stop\|p "instance name" [-i\|-k]`|在目前查詢完成執行之後，停止具有指定之名稱的 LocalDB 執行個體。<br /><br /> -i 會使用 NOWAIT 選項要求關閉 LocalDB 執行個體。<br /><br /> -k 會在未經連絡的情況下終止 LocalDB 執行個體處理序。|  
|`share\|h ["owner SID or account"] "private name" "shared name"`|使用指定的共用名稱來共用指定的私用執行個體。 如果省略使用者 SID 或帳戶名稱，會預設為目前的使用者。|  
|`unshare\|u "shared name"`|取消共用指定的共用 LocalDB 執行個體。|  
|`info\|i`|列出目前使用者擁有之所有現有的 LocalDB 執行個體，以及所有共用的 LocalDB 執行個體。|  
|`info\|i "instance name"`|列印指定之 LocalDB 執行個體的相關資訊。|  
|`versions\|v`|列出電腦上安裝的所有 LocalDB 版本。|  
|||  
|`trace\|t on\|off`|開啟及關閉追蹤。|  
  
 SqlLocalDB 會將空格視為分隔符號；你必須使用引號括住包含空格和特殊字元的執行個體名稱。 例如：  
  
 `SqlLocalDB create "My instance name with spaces"`  
  
  
