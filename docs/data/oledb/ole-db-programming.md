---
title: OLE DB 程式設計 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB [C++]
- data access [C++], OLE DB programming
- OLE DB [C++], about OLE DB
ms.assetid: 52a80d66-17a9-43a1-9b90-392ae43cea2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fb77c5b7d7f6de91f74e83c395d0fcc13ebf70e0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="ole-db-programming"></a>OLE DB 程式設計
Microsoft OLE DB 是舊版技術。新的應用程式則是必要的資料存取 API 針對連結的 SQL 伺服器。 所有其他新的應用程式應該使用 ODBC。 目前的 OLE DB provider for SQL Server 是 SQLNCLI11。DLL。 SQL Server 2016 仍會出貨的提供者。 這份文件適用於開發人員會維護已經使用 OLE DB 的現有應用程式。
  
 OLE DB 範本是 C++ 範本，可透過提供實作許多常用 OLE DB 介面的類別，讓您更輕鬆地使用高效能的 OLE DB 資料庫技術。 此範本庫分為消費者範本和提供者範本。  
  
 Visual C++ 也支援精靈建立 OLE DB 起始應用程式。  
  
 此外，您可以使用屬性來實作 OLE DB 消費者範本。  
  
|若要深入了解|請參閱|  
|-------------------------|---------|  
|使用 OLE DB 取用者範本 (概念性主題)|[OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)|  
|使用 OLE DB 提供者範本 (概念性主題)|[OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)|  
|OLE DB 範本類別和巨集|[OLE DB 範本參考](../../data/oledb/ole-db-templates.md)（Visual c + +）|  
|OLE DB 取用者屬性|[OLE DB 消費者屬性](../../windows/ole-db-consumer-attributes.md)|  
|OLE DB 介面|[OLE DB 程式設計人員參考](https://msdn.microsoft.com/en-us/library/ms713643.aspx)（在 Windows SDK)|  
|OLE DB 範本範例|[OLE DB 範本範例](http://msdn.microsoft.com/en-us/08958863-0b5f-41ad-ae99-fca7440c553c)| 
|資料存取程式設計概觀 (Visual C++)|[資料存取程式設計](../../data/data-access-programming-mfc-atl.md)|  
|ODBC 概念性主題|[開放式資料庫連接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)|  

  
## <a name="see-also"></a>另請參閱  
 [資料存取](../data-access-in-cpp.md)