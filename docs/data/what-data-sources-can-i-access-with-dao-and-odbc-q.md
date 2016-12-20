---
title: "我可以使用 DAO 和 ODBC 存取何種資料來源？ | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DAO [C++], 資料來源類型"
  - "資料 [C++], DAO"
  - "資料 [C++], ODBC"
  - "資料存取 [C++], DAO"
  - "資料來源 [C++], 可使用 DAO 和 ODBC 加以存取"
  - "資料庫 [C++], 在 DAO 中存取"
  - "FAQs [C++], 可存取的資料庫"
  - "ODBC [C++], 可存取的資料來源"
  - "ODBC 資料來源 [C++], 可存取的"
ms.assetid: c88abb45-526a-467a-a01b-d9396bd63236
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 我可以使用 DAO 和 ODBC 存取何種資料來源？
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這兩組 MFC 類別都可讓您存取各式各樣的資料來源，並撰寫獨立於資料來源的應用程式。  
  
##  <a name="_core_databases_you_can_access_with_dao"></a> 可以 DAO 存取的資料庫  
 您可使用 DAO 和 MFC DAO 類別存取下列的資料來源：  
  
-   使用 Microsoft Jet 資料庫引擎，並以 Microsoft Access 或 Microsoft Visual Basic 資料庫引擎的 1.x、2.x 和 3.0 版所建立的資料庫。  
  
-   可安裝的 ISAM 資料庫包括了：  
  
    -   dBASE III、dBASE IV 和 dBASE 5.0  
  
    -   Paradox 3.x、4.x 和 5.x 版  
  
-   開放式資料庫連接 \(ODBC\) 資料庫，包含但不限於 Microsoft SQL Server、SYBASE SQL Server 和 ORACLE Server。  若要存取 ODBC 資料庫，對於想要存取的資料庫，您必須擁有適當的 ODBC 驅動程式。  如需本版 Visual C\+\+ 中所包含 ODBC 驅動程式的清單，以及取得其他驅動程式的詳細資訊，請參閱 [ODBC 驅動程式清單](../data/odbc/odbc-driver-list.md)。  
  
-   Microsoft Excel 3.0、4.0、5.0 和 7.0 版工作表。  
  
-   Lotus WKS、WK1、WK3 和 WK4 試算表。  
  
-   文字檔。  
  
 DAO 最適合和 Microsoft Jet 資料庫引擎能讀取的資料庫搭配使用，這包含上述一切，除了 ODBC 資料來源以外。  與 Microsoft Jet \(.mdb\) 資料庫一起使用時效能最佳。  附加外部資料表至 .mdb 資料庫，比直接透過 MFC DAO 類別而不附加的方式來開啟外部資料庫還要更有效，特別是在 ODBC 資料來源內。  
  
##  <a name="_core_databases_you_can_access_with_odbc"></a> 可透過 ODBC 存取的資料庫  
 透過使用 ODBC 和 MFC ODBC 類別，只要應用程式的使用者擁有 ODBC 驅動程式，您就可存取本地或遠端的任何資料來源。有 16 位元、32 位元和 64 位元的 ODBC 驅動程式可用於許多資料來源上。  如果您使用的是 Microsoft Jet \(.mdb\) 資料庫，使用 DAO 類別會比使用 Microsoft Access ODBC 驅動程式來得有效率。  
  
## 請參閱  
 [資料存取常見問題集](../data/data-access-frequently-asked-questions-mfc-data-access.md)