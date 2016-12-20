---
title: "ODBC 和 MFC | Microsoft Docs"
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
  - "連接 [C++], 資料來源"
  - "連接 [C++], 資料庫"
  - "資料來源 [C++], 連接至"
  - "資料庫連接 [C++], MFC ODBC 類別"
  - "資料庫 [C++], 連接至"
  - "MFC [C++], ODBC 和"
  - "ODBC [C++], MFC"
ms.assetid: 98f02fd7-1235-437b-89a9-edfd0fc797f7
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ODBC 和 MFC
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  若要在 Win32 平台 \(例如 Windows NT\) 的環境中使用 MFC 資料庫類別，必須擁有適用於資料來源的適當 ODBC 驅動程式。  某些驅動程式會包含在 Visual C\+\+ 中；其他驅動程式則可自 Microsoft 和其他廠商處取得。  如需詳細資訊，請參閱 [ODBC 驅動程式清單](../../data/odbc/odbc-driver-list.md)。  
  
 這個主題會介紹 Microsoft Foundation Class \(MFC\) 程式庫的 ODBC 架構資料庫類別的主要概念，並提供類別如何共同運作的概觀。   如需 ODBC 和 MFC 的詳細資訊，請參閱下列主題：  
  
-   [連接資料來源](../../data/odbc/connecting-to-a-data-source.md)  
  
-   [選取和操作資料錄](../../data/odbc/selecting-and-manipulating-records.md)  
  
-   [顯示和操作表單中的資料](../../data/odbc/displaying-and-manipulating-data-in-a-form.md)  
  
-   [使用文件和檢視](../../data/odbc/working-with-documents-and-views.md)  
  
-   [存取 ODBC 和 SQL](../../data/odbc/access-to-odbc-and-sql.md)  
  
-   [深入瞭解 MFC ODBC 類別](../../data/odbc/further-reading-about-the-mfc-odbc-classes.md)  
  
 ODBC 架構的 MFC 資料庫類別，是為提供任何資料庫 \(具有可用的 ODBC 驅動程式\) 的存取權限所設計的。  由於該類別會使用 ODBC，因此您的應用程式可以多種不同資料格式和本機\/遠端來設定存取資料。  您不一定要撰寫用來處理不同資料庫管理系統 \(DBMS\) 的特定狀況程式碼。  只要您的使用者擁有其希望存取資料的適當 ODBC 驅動程式，他們就可以使用此程式來操作儲存在該處的資料表資料。  
  
## 請參閱  
 [開放式資料庫連接 \(ODBC\)](../../data/odbc/open-database-connectivity-odbc.md)