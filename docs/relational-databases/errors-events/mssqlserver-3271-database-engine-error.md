---
title: MSSQLSERVER_3271 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 3271 (Database Engine error)
ms.assetid: 21b8de4b-6624-4163-9561-1a6cc8fe3d51
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: dd557a391b82ceb5575ad13c6d065583105df52a
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85723635"
---
# <a name="mssqlserver_3271"></a>MSSQLSERVER_3271
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>詳細資料  
  
| 屬性 | 值 |  
| :-------- | :---- |  
|產品名稱|SQL Server|  
|事件識別碼|3271|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|DMPIO_IO_ERROR|  
|訊息文字|檔案 "%ls:" %ls 上發生無法復原的 I/O 錯誤。|  
  
## <a name="explanation"></a>說明  
這是作業系統在備份或還原作業期間執行 I/O 時引發錯誤時所發生的一般錯誤。 大部分情況下，造成這項錯誤的原因純粹因為備份媒體已滿。  
  
此錯誤可能包括作業系統指出磁碟已滿的其他文字。 以協力廠商軟體執行備份或還原作業時，可能會出現另一則訊息，指出備份已經失敗。 這則訊息看起來可能與下列文字類似：  
  
```  
"2005-08-02 16:05:16.04 spid55 Error: 18210, Severity: 16, State: 1.  
 2005-08-02 16:05:16.04 spid55 BackupVirtualDeviceFile  
::RequestDurableMedia: Flush failure on backup device 'VDINULL'.   
Operating system error 995(The I/O operation has been aborted because   
of either a thread exit or an application request.)."  
```  
  
這則訊息代表備份軟體要求您結束備份或還原作業。  
  
## <a name="user-action"></a>使用者動作  
依照需要執行下列工作：  
  
-   檢閱這則訊息之前的基本系統錯誤訊息和 SQL Server 錯誤訊息，找出失敗的原因。  
  
-   確定備份和還原媒體具有足夠的空間。  
  
-   更正協力廠商備份和還原軟體引發的任何錯誤。  
  
