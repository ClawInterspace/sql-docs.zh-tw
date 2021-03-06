---
title: 依書簽更新、刪除或提取 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- updating by bookmarks [ODBC]
- result sets [ODBC], bookmarks
- fetches [ODBC], by bookmarks [ODBC]
- deleting by bookmarks [ODBC]
- bookmarks [ODBC]
ms.assetid: e2ee58d7-c28f-435f-b537-06207215dd2f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5e94a98bb577ef906afbb04539761fd07d15f772
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "81286148"
---
# <a name="updating-deleting-or-fetching-by-bookmark"></a>依書籤更新、刪除或擷取
書簽可以用來識別要在結果集內更新的資料、從結果集中刪除，或從結果集提取到資料列集緩衝區。 這些作業是透過呼叫**SQLBulkOperations** ，並使用 SQL_UPDATE_BY_BOOKMARK、SQL_DELETE_BY_BOOKMARK 或 SQL_FETCH_BY_BOOKMARK 的*Option*引數來執行。 這些作業中使用的書簽會儲存在資料列集緩衝區的資料行0中。 當依書簽更新時，會從資料列集緩衝區中抓取結果集資料行更新的資料。 如需詳細資訊，請參閱[使用 SQLBulkOperations 更新資料](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md)。
