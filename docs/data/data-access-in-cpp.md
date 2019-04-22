---
title: Visual C++ 中的資料存取
ms.date: 03/28/2017
helpviewer_keywords:
- Visual C++, data access applications
- databases [C++]
- OLE DB [C++], data access technologies
- data [C++], data access technologies
- data access [C++], class libraries for databases
ms.assetid: 95da6237-bbe2-480a-ae50-3a520051ceff
ms.openlocfilehash: 142d067b6fbc9e2357ff8fc23fd931a1194477e9
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59041250"
---
# <a name="data-access-in-visual-c"></a>Visual C++ 中的資料存取

幾乎所有 SQL 和 NoSQL 資料庫產品都會提供原生 C++ 應用程式的介面。 此業界標準介面是 ODBC，所有主要的 SQL 資料庫產品和許多 NoSQL 產品均提供相關支援。 對於非 Microsoft 產品，請洽詢廠商以取得詳細資訊。 此外，還有具各種授權條款的協力廠商程式庫可供使用。

從 2011 年開始，Microsoft 已經過調整，並以 ODBC 作為原生應用程式連線到內部部署和雲端 Microsoft SQL Server 資料庫的標準。 如需詳細資訊，請參閱[資料存取程式設計 \(MFC-ATL\)](data-access-programming-mfc-atl.md)。 C++/CLI 程式庫可以使用原生 ODBC 驅動程式或 ADO.NET。 如需詳細資訊，請參閱[使用 ADO.NET 進行資料存取 (C++/CLI)](../dotnet/data-access-using-adonet-cpp-cli.md) 和[存取 Visual Studio 中的資料](https://docs.microsoft.com/visualstudio/data-tools/accessing-data-in-visual-studio)。

## <a name="in-this-section"></a>本節內容

[資料存取程式設計 (MFC/ATL)](data-access-programming-mfc-atl.md)<br/>
說明使用 Visual C++ 的舊版資料存取設計程式，慣用方法為使用其中一個類別庫，例如 Active Template Class Library (ATL) 或 Microsoft Foundation Class (MFC) 程式庫，這可以簡化使用資料庫 API。

[開放式資料庫連接 (ODBC)](odbc/open-database-connectivity-odbc.md)<br/>
Microsoft Foundation Classes (MFC) 程式庫提供可以使用開放式資料庫連接 (ODBC) 進行程式設計的類別。

[OLE DB 程式設計](oledb/ole-db-programming.md)<br/>
大部分傳統的介面，用它仍然需要在某些情況下，特別是當您對連結的伺服器進行程式設計時。

## <a name="related-topics"></a>相關主題

[連接到 SQL Database 使用 C 和C++](/azure/sql-database/sql-database-develop-cplusplus-simple)<br/>
連接到 Azure SQL Database 中，從 C 或C++應用程式。

[適用於 Microsoft Azure 儲存體用戶端程式庫C++](https://github.com/Azure/azure-storage-cpp)<br/>
[Azure 儲存體](/azure/storage/storage-introduction)是新式應用程式的雲端儲存解決方案，這些應用程式依賴持久性、可用性和延展性來符合客戶的需求。 使用 C++ 的 Azure 儲存體用戶端程式庫，從 C++ 連線到 Azure 儲存體。

[ODBC Driver 13.1 for SQL Server-Windows 發行](https://blogs.msdn.microsoft.com/sqlnativeclient/2016/08/01/announcing-the-odbc-driver-13-1-for-sql-server)<br/>
此最新的 ODBC 驅動程式為 C/C++ 架構應用程式，提供對 Microsoft SQL Server 2016 和 Microsoft Azure SQL Database 的強固資料存取。 提供支援的功能包括 always encrypted、 Azure Active Directory 和 AlwaysOn 可用性群組。 也適用於 MacOS 及 Linux。

[SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client-programming)<br/>
SQL Server Native Client 是支援 SQL Server 2005 到 SQL Server 2014 的獨立資料存取應用程式開發介面 (API)，可用於 OLE DB 和 ODBC。 新的應用程式應該使用 ODBC Driver 13.1 for SQL Server。

[Microsoft Azure C 和C++開發人員中心](https://azure.microsoft.com/develop/cpp/)<br/>
Azure 可讓您使用最愛的工具，以更具有彈性、延展性及可靠的方式，輕鬆建置 C++ 應用程式。

[如何使用從 Blob 儲存體C++](https://docs.microsoft.com/azure/storage/storage-c-plus-plus-how-to-use-blobs)<br/>
Azure Blob 儲存體是可將非結構化的資料儲存在雲端作為物件/Blob 的服務。 Blob 儲存體可以儲存任何類型的文字或二進位資料，例如文件、媒體檔案或應用程式安裝程式。 Blob 儲存體也稱為物件儲存體。

[ ODBC 程式設計人員參考](https://docs.microsoft.com/sql/odbc/reference/odbc-programmer-s-reference)<br/>
ODBC 介面是專為搭配 C 程式設計語言使用所設計。 使用 ODBC 介面跨越三個區域：SQL 陳述式、 ODBC 函式呼叫和 C 程式設計。

## <a name="see-also"></a>另請參閱

[Visual C++](../overview/visual-cpp-in-visual-studio.md)
