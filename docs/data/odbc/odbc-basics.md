---
title: "ODBC 的基本概念 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ODBC 元件"
  - "ODBC 元件, 必要元件"
  - "ODBC 資料指標程式庫 [ODBC], ODBC 元件"
  - "ODBC, 關於 ODBC"
  - "ODBC, 元件"
ms.assetid: ec529702-0fb2-4754-b8de-d1efa8eca18f
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# ODBC 的基本概念
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個主題會提供開放式資料庫連接 \(ODBC\) 的基本概念：  
  
-   [ODBC 使用資料庫類別的方式](../../data/odbc/odbc-and-the-database-classes.md)  
  
-   [ODBC 驅動程式使用動態集的方式](../../data/odbc/odbc-driver-requirements-for-dynasets.md)  
  
-   [您要轉散發應用程式所需的 ODBC 元件](../../data/odbc/redistributing-odbc-components-to-your-customers.md)  
  
 您可能也想要參閱 [ODBC：ODBC 資料指標程式庫](../../data/odbc/odbc-the-odbc-cursor-library.md)相關主題。  
  
> [!NOTE]
>  ODBC 資料來源可透過 MFC ODBC 類別存取 \(如本主題所述\)，或透過 MFC 資料存取物件 \(DAO\) 類別存取。  
  
> [!NOTE]
>  MFC ODBC 類別可支援 Unicode 和多執行緒。  如需多執行緒支援的詳細資訊，請參閱 [ODBC 類別和執行緒](../../data/odbc/odbc-classes-and-threads.md)。  
  
 ODBC 是一種呼叫層級介面，可允許應用程式在有 ODBC 驅動程式情況下存取資料庫的資料。  您可以使用 ODBC，來建立可存取任何資料庫的資料庫應用程式 \(使用者須擁有 ODBC 驅動程式\)。  ODBC 可提供一個允許您的應用程式獨立於來源資料庫管理系統 \(DBMS\) 的 API。  
  
 ODBC 是 Microsoft Windows Open Services Architecture \(WOSA\) 的資料庫部分，WOSA 是一種介面，可允許 Windows 架構桌面應用程式連接至多重運算環境，而無須為每種平台重新撰寫應用程式。  
  
 下面是 ODBC 的元件：  
  
-   ODBC API  
  
     一個用來在 DBMS 上存取資料的函式呼叫 \(Function Call\) 程式庫、一組錯誤代碼和標準 \([SQL](../../data/odbc/sql.md)\) 語法。  
  
-   ODBC 驅動程式管理員  
  
     一種可為應用程式載入 ODBC 資料庫驅動程式的動態連結程式庫 \(Odbc32.dll\)。  這個 DLL 可以外掛到您的應用程式上。  
  
-   ODBC 資料庫驅動程式  
  
     一或多個用來處理特定資料庫管理系統 \(DBMS\) ODBC 函式呼叫的 DLL。  如需所提供驅動程式的清單，請參閱 [ODBC 驅動程式清單](../../data/odbc/odbc-driver-list.md)。  
  
-   [ODBC 資料指標程式庫](../../data/odbc/odbc-the-odbc-cursor-library.md)  
  
     一種位於 ODBC 驅動程式管理員和驅動程式之間，且可處理資料捲動的動態連結程式庫 \(Odbccr32.dll\)。  
  
-   [ODBC 管理員](../../data/odbc/odbc-administrator.md)  
  
     一種可設定資料庫管理系統 \(DBMS\) 的工具使 DBMS 成為一個應用程式資料來源的工具。  
  
 應用程式可以透過特別為 DBMS 所撰寫的 ODBC 驅動程式，而非直接使用 DBMS 的方式，來保持 DBMS 的獨立性。  驅動程式會將呼叫轉譯成 DBMS 可使用的命令，以便簡化開發人員的工作，並且可以使用大範圍的資料來源。  
  
 資料庫類別可支援任何一種您擁有 ODBC 驅動程式的資料來源。  也就是說，其中可能包括了一個關聯式資料庫、索引循序存取方法 \(ISAM\) 資料庫、Microsoft Excel 試算表或是一個文字檔。  ODBC 驅動程式可以管理資料來源的連接，以及用來選取資料庫資料錄的 SQL。  
  
 如需本版 Visual C\+\+ 中所包含 ODBC 驅動程式的清單，以及取得其他驅動程式的詳細資訊，請參閱 [ODBC 驅動程式清單](../../data/odbc/odbc-driver-list.md)。  
  
## 請參閱  
 [開放式資料庫連接 \(ODBC\)](../../data/odbc/open-database-connectivity-odbc.md)