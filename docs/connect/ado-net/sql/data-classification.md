---
title: SqlClient 中的資料探索與分類
description: 描述如何檢查 SQL Server 資料庫是否支援資料分類，以及如何透過 SqlDataReader 物件存取資料分類資訊。
ms.date: 06/15/2020
dev_langs:
- csharp
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: johnnypham
ms.author: v-jopha
ms.reviewer: ''
ms.openlocfilehash: 27b9c232fe785d3c016848f3bb952236b8e7cd75
ms.sourcegitcommit: 6b3569977b034554883a94d73d1c4df6e2f74fe2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2020
ms.locfileid: "85110103"
---
# <a name="data-discovery-and-classification-in-sqlclient"></a>SqlClient 中的資料探索與分類

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

[資料探索與分類](https://docs.microsoft.com/sql/relational-databases/security/sql-data-discovery-and-classification?view=sql-server-2017)是一組進階服務，用於探索、分類、標記和報告資料庫中的敏感性資料。 SqlClient 提供 API，可在基礎來源支援時公開唯讀資料探索和分類資訊。 這項資訊可透過 SqlDataReader 存取。

此範例應用程式會示範如何存取 SqlDataReader 的資料分類屬性。

[!code-csharp [SqlDataReader_DataDiscoveryAndClassification#1](~/../sqlclient/doc/samples/SqlDataReader_DataDiscoveryAndClassification.cs#1)]

**另請參閱**  

 [SQL Server 功能和 ADO.NET](sql-server-features-adonet.md)   
