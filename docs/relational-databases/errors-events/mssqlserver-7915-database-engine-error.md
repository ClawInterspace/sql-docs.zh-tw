---
title: MSSQLSERVER_7915 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 7915 (Database Engine error)
ms.assetid: 63338587-7dd3-40e6-b70e-d8ae18fff47b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c640e33c823ab6f4e6301793aca9fb427f9e7aa5
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85791044"
---
# <a name="mssqlserver_7915"></a>MSSQLSERVER_7915
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>詳細資料  
  
| 屬性 | 值 |  
| :-------- | :---- |  
|產品名稱|SQL Server|  
|事件識別碼|7915|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|DBCC2_REPAIR_IAM_CHAIN_REBUILT|  
|訊息文字|修復:物件識別碼 O_ID，索引識別碼 I_ID，分割區識別碼 PN_ID，配置單位識別碼 A_ID (類型 TYPE) 的 IAM 鏈結已在頁面 P_ID 之前截斷，且將會重建。|  
  
## <a name="explanation"></a>說明  
這是由 REPAIR 傳送的參考用資訊，指出已經修補指定的索引配置對應 (IAM) 鏈結，因此可以重建該鏈結。 這項修補動作可能已經要求配置 IAM 鏈結的新標頭，或是從鏈結中移除錯誤的頁面。  
  
## <a name="user-action"></a>使用者動作  
None  
  
