---
title: "MFC 資料庫程式撰寫模型是什麼？ | Microsoft Docs"
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
  - "DAO [C++], MFC"
  - "資料存取 [C++], 技術"
  - "資料庫 [C++], MFC"
  - "MFC [C++], 資料庫應用程式"
  - "ODBC [C++], MFC"
  - "ODBC 類別 [C++], MFC 資料庫類別"
ms.assetid: f6f15bb8-4115-41f2-ad68-036e74a11bd9
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC 資料庫程式撰寫模型是什麼？
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

雖然 MFC 實作 DAO 和 ODBC 的內部方式有很大的差異，它們的介面卻非常類似，因此您可相當輕鬆地將應用程式從一個移植至另一個，特別是從 ODBC 移植至 DAO。  如需從 ODBC 移植至 DAO 的詳細資訊，請參閱[技術提示 55](../mfc/tn055-migrating-mfc-odbc-database-class-applications-to-mfc-dao-classes.md)。  MFC 中的 DAO 和 ODBC 介面和 Visual Basic 的介面也非常類似。  
  
 MFC 程式撰寫模型 \(Programming Model\) 針對每個開放資料庫都提供一個資料庫物件。  資料庫物件代表您到資料庫的連接。  您可使用資料錄集物件來查詢和更新。  DAO 提供了其他的物件，以便使用資料表結構、儲存查詢以重複使用等等，這些將於稍後說明。  MFC 為每個這類物件提供類別：有一組類別針對 DAO，針對 ODBC 則有另一組。  
  
 使用 MFC 可更輕鬆地存取資料。  DAO 和 ODBC 資料庫類別提供了高階的抽象，讓您不需直接使用 DAO 或 ODBC。  寫入它們的 API 比使用 MFC 類別更複雜。  如果您所撰寫的應用程式是相當簡單的小型應用程式更是如此。  
  
 資料庫類別會將下列元件加入至 MFC 類別庫內：  
  
-   提供高階 API 的 C\+\+ 資料庫類別，以透過 DAO 或 ODBC 來存取資料庫  
  
-   應用程式精靈和 \[加入類別\] 的擴充功能，可建立應用程式特定的資料庫類別  
  
-   說明類別和精靈用法的範例程式  
  
-   線上文件包含了概觀、程式設計主題的文件和類別參考資料  
  
 如需這些元件的詳細資訊，請參閱 [ODBC 和 MFC](../data/odbc/odbc-and-mfc.md)。  
  
 如需詳細資訊，請參閱：  
  
-   [在 DAO 和 ODBC 之間選擇](../data/should-i-use-dao-or-odbc-q.md)  
  
-   在 DAO 和 ODBC 內[資料庫定義語言 \(DDL\) 和資料庫管理語言 \(DML\) 的可用性](../data/are-ddl-and-dml-supported-q.md)  
  
-   [安裝 MFC 資料庫支援](../data/installing-mfc-database-support.md)  
  
-   MFC 中的 [ODBC](../data/odbc/odbc-and-mfc.md) 類別  
  
-   [MFC 資料存取程式設計文件](../data/mfc-database-documentation.md)  
  
-   [MFC 如何實作 ODBC](../data/odbc/odbc-and-mfc.md)  
  
## 請參閱  
 [資料存取常見問題集](../data/data-access-frequently-asked-questions-mfc-data-access.md)