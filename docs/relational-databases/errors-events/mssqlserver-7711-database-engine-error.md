---
title: MSSQLSERVER_7711 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 7711 (Database Engine error)
ms.assetid: a5c7cd6e-18d6-47ef-902b-db9dd64bba34
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 03c60252186a6e8177d379c895ec8eade565a5cd
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85780191"
---
# <a name="mssqlserver_7711"></a>MSSQLSERVER_7711
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>詳細資料  
  
| 屬性 | 值 |  
| :-------- | :---- |  
|產品名稱|SQL Server|  
|事件識別碼|7711|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|PRT_RANGE_OVERLAP|  
|訊息文字|資料表或索引或是它的其中一個資料分割已指定 DATA_COMPRESSION 選項一次以上。|  
  
## <a name="explanation"></a>說明  
下列其中一個陳述式中的 DATA_COMPRESSION 選項發生錯誤：  
  
-   CREATE TABLE  
  
-   ALTER TABLE  
  
-   CREATE INDEX  
  
-   ALTER INDEX  
  
如果分割了引用的資料表或索引，則表示其中至少一個分割區已列出 DATA_COMPRESSION 選項一次以上。 如果此資料表或索引未分割，則表示 DATA_COMPRESSION 選項已經引用一次以上。  
  
## <a name="user-action"></a>使用者動作  
如果是已分割的資料表或索引，請確定每一個分割區只指定 DATA_COMPRESSION 選項一次。 如果是未分割的資料表或索引，只能在陳述式中使用 DATA_COMPRESSION 選項一次。  
  
