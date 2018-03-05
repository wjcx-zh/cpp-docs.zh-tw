---
title: "Visual c + + 中的資料存取 |Microsoft 文件"
ms.custom: 
ms.date: 03/28/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, data access applications
- databases [C++]
- OLE DB [C++], data access technologies
- data [C++], data access technologies
- data access [C++], class libraries for databases
ms.assetid: 95da6237-bbe2-480a-ae50-3a520051ceff
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: eaefb5f3ed8bd0c586e42527d47918dbb0dd5a57
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="data-access-in-visual-c"></a>Visual C++ 中的資料存取

幾乎所有 SQL 和 NoSQL 資料庫產品都會提供原生 C++ 應用程式的介面。 此業界標準介面是 ODBC，所有主要的 SQL 資料庫產品和許多 NoSQL 產品均提供相關支援。 對於非 Microsoft 產品，請洽詢廠商以取得詳細資訊。 此外，還有具各種授權條款的協力廠商程式庫可供使用。

從 2011 年開始，Microsoft 已經過調整，並以 ODBC 作為原生應用程式連線到內部部署和雲端 Microsoft SQL Server 資料庫的標準。 如需詳細資訊，請參閱[資料存取程式設計 \(MFC-ATL\)](data-access-programming-mfc-atl.md)。 C++/CLI 程式庫可以使用原生 ODBC 驅動程式或 ADO.NET。 如需詳細資訊，請參閱[使用 ADO.NET 進行資料存取 (C++/CLI)](/dotnet/data-access-using-adonet-cpp-cli.md) 和[存取 Visual Studio 中的資料](https://docs.microsoft.com/visualstudio/data-tools/accessing-data-in-visual-studio)。

## <a name="in-this-section"></a>本節內容
[資料存取程式設計 (MFC/ATL)](data-access-programming-mfc-atl.md)描述舊版資料存取程式設計，Visual c + +，其中的慣用的方法是使用其中一種類別庫，例如 Active Template 類別 Library (ATL) 或 Microsoft Foundation Class (MFC) 程式庫，可簡化使用資料庫 Api。

[開啟資料庫連接 (ODBC)](odbc/open-database-connectivity-odbc.md) Microsoft Foundation Classes (MFC) 程式庫提供程式設計開放式資料庫連接 (ODBC) 的類別。

[OLE DB 程式設計](oledb/ole-db-programming.md)仍然需要在某些情況下，特別是當您對進行程式設計時的大部分傳統介面連結伺服器。

## <a name="related-topics"></a>相關主題
[連接到 SQL Database 使用 C 和 c + +](/azure/sql-database/sql-database-develop-cplusplus-simple)從 C 或 c + + 應用程式連接至 Azure SQL Database。

[Microsoft Azure 儲存體用戶端程式庫的 c + +](https://github.com/Azure/azure-storage-cpp)
[Azure 儲存體](/azure/storage/storage-introduction)是雲端儲存體解決方案，依賴持續性、 可用性和延展性，以符合需求的現代應用程式及其客戶。 使用 C++ 的 Azure 儲存體用戶端程式庫，從 C++ 連線到 Azure 儲存體。

[ODBC Driver 13.1 for SQL Server-Windows 發行](https://blogs.msdn.microsoft.com/sqlnativeclient/2016/08/01/announcing-the-odbc-driver-13-1-for-sql-server)最新的 ODBC 驅動程式會提供 Microsoft SQL Server 2016 Microsoft Azure SQL database 穩固的資料存取 C/c + + 架構應用程式。 提供一律加密功能，包括支援、 Azure Active Directory 和 AlwaysOn 可用性群組。 也適用於 MacOS 及 Linux。     
 
[SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client-programming) SQL Server Native Client 是獨立的資料存取應用程式開發介面 (API)，用於 OLE DB 和 ODBC 支援 SQL Server 2005 中透過 SQL Server 2014。 新的應用程式應該使用 ODBC Driver 13.1 for SQL Server。

[Microsoft Azure C 和 c + + 開發人員中心](https://azure.microsoft.com/develop/cpp/)Azure 可讓您輕鬆地建置 c + + 應用程式增加的彈性、 延展性與可靠性，使用您喜愛的工具。    

[如何使用 Blob 儲存體從 c + +](https://docs.microsoft.com/azure/storage/storage-c-plus-plus-how-to-use-blobs) Azure Blob 儲存體是雲端中儲存非結構化的資料，做為物件/blob 服務。 Blob 儲存體可以儲存任何類型的文字或二進位資料，例如文件、媒體檔案或應用程式安裝程式。 Blob 儲存體也稱為物件儲存體。

[ODBC 程式設計人員參考](https://docs.microsoft.com/sql/odbc/reference/odbc-programmer-s-reference)ODBC 介面設計用於與 C 程式設計語言。 ODBC 介面可用於下列三方面︰SQL 陳述式、ODBC 函式呼叫和 C 程式設計。

## <a name="see-also"></a>請參閱
[Visual C++](../visual-cpp-in-visual-studio.md)
