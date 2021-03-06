---
title: SQL 語句的互通性 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC]
- interoperability of SQL statements [ODBC], about interoperability
ms.assetid: 3b24c499-829c-4e65-90cf-a3a0f6d0a186
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d3d7a76c67096d2e76fe1cd3d4b15f73122699e7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "81302799"
---
# <a name="interoperability-of-sql-statements"></a>SQL 陳述式的互通性
如同應用程式的其餘部分，SQL 語句可以互通或 DBMS 特定。 就像應用程式的其餘部分，選擇可互通的 SQL 語句需要如何依賴應用程式的類型。 自訂應用程式較不可能使用互通的 SQL 語句，因為它們通常是設計來利用一或多個 Dbms 的功能。 泛型應用程式會使用可互通的 SQL 語句，因為它們是設計來與各種 Dbms 搭配運作。 和垂直應用程式通常會落在其間的某處，而需要特定層級的功能，但使用可互通的 SQL 語句。  
  
 此章節包含下列主題。  
  
-   [選擇 SQL 文法](../../../odbc/reference/develop-app/choosing-an-sql-grammar.md)  
  
-   [建構可互通的 SQL 陳述式](../../../odbc/reference/develop-app/constructing-interoperable-sql-statements.md)
