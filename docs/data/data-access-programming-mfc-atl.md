---
title: 資料存取程式設計 (MFC-ATL)
ms.date: 11/16/2018
helpviewer_keywords:
- MFC [C++], data access applications
- databases [C++], MFC
- OLE DB [C++], data access technologies
- data [C++], data access technologies
- data access [C++], class libraries for databases
ms.assetid: def97b2c-b5a6-445f-afeb-308050fd4852
ms.openlocfilehash: e71e16bef29239e0c6a391b2d5e2129042cd52fa
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221853"
---
# <a name="data-access-programming-mfcatl"></a>Data Access Programming (MFC/ATL)

Visual C++ 多年來提供了數種使用資料庫的方式。 在 2011 年，Microsoft 宣佈它正在校準開放式資料庫連接 (ODBC) 作為慣用的技術，以從原生程式碼存取 SQL Server 產品。 ODBC 是一種業界標準，使用它可讓您在多個平台和資料來源間自由攜帶程式碼。 大多數的 SQL 資料庫產品和許多 NoSQL 產品都支援 ODBC。 您可以呼叫低階的 ODBC API 直接使用 ODBC，或者可以使用 MFC ODBC 包裝函式類別，或協力廠商的 C++ 包裝函式程式庫。

OLE DB 是以 COM 規格為基礎的低階高效 API，只有 Windows 提供支援。 如果您的程式正在存取[連結的伺服器](/sql/relational-databases/linked-servers/linked-servers-database-engine)，請使用 OLE DB。 ATL 提供 OLE DB 範本，讓您更容易建立自訂的 OLE DB 提供者和取用者。 Microsoft SQL Server 的最新提供者可以文件中找到[OLE DB Driver for SQL Server](/sql/connect/oledb/oledb-driver-for-sql-server)。

## <a name="porting-data-applications"></a>移植資料應用程式

如果您的舊版應用程式會使用 OLE DB 或更高階的 ADO 介面連接到 SQL Server，您應該考慮移轉至最新[OLE DB Driver for SQL Server](/sql/connect/oledb/oledb-driver-for-sql-server)以利用最新的 SQL Server 功能。 另一個替代方式，如果您不需要跨平台可攜性或最新的 SQL Server 功能，您可以可能是使用 Microsoft OLE DB Provider for ODBC (MSDASQL)。  MSDASQL 讓建置在 OLE DB 和 ADO (在內部使用 OLEDB) 上的應用程式透過 ODBC 驅動程式存取資料來源。 和所有的轉譯層一樣，MSDASQL 會影響資料庫效能。 您應該測試以判斷此影響對您的應用程式是否過大。 MSDASQL 隨附於 Windows 作業系統，而 Windows Server 2008 和 Windows Vista SP1 是第一批包含此技術 64 位元版本的 Windows 版本。

如果您C++應用程式連接到 SQL Server 或 Azure SQL Database，透過 ODBC，它應該使用[最新的 ODBC 驅動程式](/sql/connect/odbc/download-odbc-driver-for-sql-server)。

如果您使用 C++/CLI，就可以繼續像平常一樣使用 ADO.NET。 如需詳細資訊，請參閱[使用 ADO.NET 存取資料 (C++/CLI)](../dotnet/data-access-using-adonet-cpp-cli.md) 和[存取 Visual Studio 中的資料](/visualstudio/data-tools/accessing-data-in-visual-studio)。

- 除了 ODBC 包裝函式類別，MFC 也提供資料存取物件 (DAO) 包裝函式類別以連接到 Access 資料庫。  不過，DAO 已淘汰。 所有以 CDaoDatabase 或 CDaoRecordset 為基礎的程式碼都應該升級。

如需 Microsoft Windows 資料存取技術記錄的相關資訊，請參閱 [Microsoft Data Access Components (Wikipedia)](https://en.wikipedia.org/wiki/Microsoft_Data_Access_Components) (Microsoft 資料存取元件 (維基百科))。

## <a name="see-also"></a>另請參閱

[資料存取](data-access-in-cpp.md)<br/>
[Microsoft Open Database Connectivity (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc) (Microsoft 開放式資料庫連接 (ODBC))<br/>
