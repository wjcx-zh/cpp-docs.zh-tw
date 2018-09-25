---
title: 移植資料應用程式 | Microsoft Docs
ms.custom: ''
ms.date: 05/12/2017
ms.technology:
- devlang-cpp
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], data access applications
- databases [C++], MFC
- OLE DB [C++], data access technologies
- data [C++], data access technologies
- data access [C++], class libraries for databases
ms.assetid: 8d10c285-c13f-4e6e-a09e-5ee0f2666b44
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bc789cb37b51f89022a83d1ba34bb67ae32a206e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46391588"
---
# <a name="porting-data-applications"></a>移植資料應用程式
Visual C++ 多年來提供了數種使用資料庫的方式。 2011 年，Microsoft 宣佈它正在校準 ODBC 做為慣用技術，以從原生程式碼存取 SQL Server 產品。 ODBC 是一種業界標準，使用它可讓您在多個平台和資料來源間自由攜帶程式碼。 大多數的 SQL 資料庫產品和許多 NoSQL 產品都支援 ODBC。 您可以呼叫低階的 ODBC API 直接使用 ODBC，或者可以使用 MFC ODBC 包裝函式類別，或協力廠商的 C++ 包裝函式程式庫。 

OLE DB 是以 COM 規格為基礎的低階高效 API，只有 Windows 提供支援。 如果您的程式正在存取[連結的伺服器](/sql/relational-databases/linked-servers/linked-servers-database-engine)，請使用 OLE DB。 ATL 提供 OLE DB 範本，讓您更容易建立自訂的 OLE DB 提供者和取用者。 OLE DB 最新版本隨附於 SQL Native Client 11。  

如果舊版應用程式使用 OLE DB 或更高階的 ADO 介面連接到 SQL Server，而您存取的不是連結的伺服器，您應該考慮於近期移轉到 ODBC。 如果您不需要跨平台可攜性或最新的 SQL Server 功能，您可能可以使用 Microsoft OLE DB Provider for ODBC (MSDASQL)。  MSDASQL 讓建置在 OLE DB 和 ADO (在內部使用 OLEDB) 上的應用程式透過 ODBC 驅動程式存取資料來源。 和所有的轉譯層一樣，MSDASQL 會影響資料庫效能。 您應該測試以判斷此影響對您的應用程式是否太過。 MSDASQL 隨附於 Windows 作業系統，而 Windows Server 2008 和 Windows Vista SP1 是第一批包含此技術 64 位元版本的 Windows 版本。

將 OLE DB 和 ODBC 驅動程式封裝在單一 DLL 的 SQL Native Client 元件 (SNAC)，已被 ODBC 應用程式取代。 SNAC 的 SQL Server 2012 版本 (SQLNCLI11.DLL) 隨附於 SQL Server 2016，因為其他的 SQL Server 元件都依存於它。 但是，透過 ODBC 連接到 SQL Server 或 Azure SQL Database 的新 C++ 應用程式，都應該使用[最新版的 ODBC 驅動程式](https://docs.microsoft.com/en-us/sql/connect/odbc/download-odbc-driver-for-sql-server)。 如需詳細資訊，請參閱 [SQL Server Native Client Programming](/sql/relational-databases/native-client/sql-server-native-client-programming) (SQL Server Native Client 程式設計)

如果您使用 C++/CLI，就可以繼續像平常一樣使用 ADO.NET。 如需詳細資訊，請參閱[使用 ADO.NET 存取資料 (C++/CLI)](../dotnet/data-access-using-adonet-cpp-cli.md) 和[存取 Visual Studio 中的資料](/visualstudio/data-tools/accessing-data-in-visual-studio)。  
  
- 除了 ODBC 包裝函式類別，MFC 也提供資料存取物件 (DAO) 包裝函式類別連接到 Access 資料庫。  不過，DAO 已淘汰。 所有以 `CDaoDatabase` 或 `CDaoRecordset` 為基礎的程式碼均應升級。 

如需 Microsoft Windows 資料存取技術記錄的相關資訊，請參閱 [Microsoft Data Access Components (Wikipedia)](https://en.wikipedia.org/wiki/Microsoft_Data_Access_Components) (Microsoft 資料存取元件 (維基百科))。  

## <a name="see-also"></a>請參閱  
 
[Visual C++ 中的資料存取](../data/data-access-in-cpp.md)<br/>
[Microsoft Open Database Connectivity (ODBC)](https://docs.microsoft.com/sql/odbc/microsoft-open-database-connectivity-odbc) (Microsoft 開放式資料庫連接 (ODBC))<br/>
[Data Access Technologies Road Map](https://msdn.microsoft.com/library/ms810810.aspx) (資料存取技術藍圖)  