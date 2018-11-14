---
title: OLE DB 程式設計
ms.date: 10/22/2018
helpviewer_keywords:
- OLE DB [C++]
- data access [C++], OLE DB programming
- OLE DB [C++], about OLE DB
ms.assetid: 52a80d66-17a9-43a1-9b90-392ae43cea2b
ms.openlocfilehash: 59bee1c204d2f101d8175ff42c78ca4bbdcaeb4c
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2018
ms.locfileid: "51523139"
---
# <a name="ole-db-programming"></a>OLE DB 程式設計

Microsoft OLE DB 是舊版技術;對於新的應用程式是連結的 SQL 伺服器的所需的資料存取 API。 所有其他新的應用程式應該使用 ODBC。 目前的 OLE DB provider for SQL Server 是 SQLNCLI11。DLL。 SQL Server 2016 仍會出貨的提供者。 這份文件適用於開發人員會維護已使用 OLE DB 的現有應用程式。

OLE DB 範本是 C++ 範本，可透過提供實作許多常用 OLE DB 介面的類別，讓您更輕鬆地使用高效能的 OLE DB 資料庫技術。 此範本庫分為消費者範本和提供者範本。

Visual C++ 也支援精靈建立 OLE DB 起始應用程式。

此外，您可以使用屬性來實作 OLE DB 消費者範本。

|深入了解|請參閱|
|-------------------------|---------|
|使用 OLE DB 取用者範本 (概念性主題)|[OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)|
|使用 OLE DB 提供者範本 (概念性主題)|[OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)|
|OLE DB 範本類別和巨集|[OLE DB 範本參考](../../data/oledb/ole-db-templates.md)（Visual c + +）|
|OLE DB 取用者屬性|[OLE DB 消費者屬性](../../windows/ole-db-consumer-attributes.md)|
|OLE DB 介面|[OLE DB 程式設計人員參考](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming(v%3dvs.85))（在 Windows SDK)|
|OLE DB 範本範例|[OLE DB 範本範例](https://github.com/Microsoft/VCSamples)|
|資料存取程式設計概觀 (Visual C++)|[資料存取程式設計](../../data/data-access-programming-mfc-atl.md)|
|ODBC 概念性主題|[開放式資料庫連接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)|

## <a name="see-also"></a>另請參閱

[資料存取](../data-access-in-cpp.md)