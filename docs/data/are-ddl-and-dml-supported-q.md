---
title: "可否支援 DDL 和 DML？ | Microsoft Docs"
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
  - "MFC ODBC 中的資料操作語言 [C++]"
  - "資料庫 [C++], 在 DAO 中存取"
  - "資料庫 [C++], DDL 存取"
  - "資料庫 [C++], DML 存取"
  - "DDL [C++], MFC 支援"
  - "DML [C++]"
  - "DML [C++], MFC ODBC"
ms.assetid: 07f96d81-78d4-4bec-9138-b15d68fd5ce0
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 可否支援 DDL 和 DML？
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC DAO 類別可支援兩類資料庫存取：  
  
-   **資料定義語言 \(DDL\)**：您可建立和刪除資料庫、建立和刪除資料表、定義資料表欄位和索引，以及採取其他會影響資料庫結構的動作。  
  
-   **資料操作語言 \(DML\)**：您可執行查詢、加入、刪除和編輯資料錄，或是操作資料庫的內容。  
  
 MFC ODBC 類別僅支援 DML，不過您也可直接呼叫 ODBC API 函式來執行 DDL 工作。  
  
## 請參閱  
 [資料存取常見問題集](../data/data-access-frequently-asked-questions-mfc-data-access.md)