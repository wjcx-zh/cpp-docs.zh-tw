---
title: "結構描述 (MFC 資料存取) | Microsoft Docs"
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
  - "資料庫結構描述 [C++]"
  - "資料庫結構描述 [C++], 關於資料庫結構描述"
  - "資料庫 [C++], 結構描述"
  - "結構描述 [C++], 資料庫"
  - "結構 [C++]"
  - "結構 [C++], 資料庫"
ms.assetid: 7d17e35f-1ccf-4853-b915-5b8c7a45b9ee
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 結構描述 (MFC 資料存取)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

資料庫結構描述說明資料庫中的資料表和資料庫檢視的目前結構。  一般情況下，精靈產生的程式碼會假設資料錄集所存取的資料表之結構描述將不會變更，但是資料庫類別可以處理某些結構描述變更，例如加入、重新排列或刪除未繫結的資料行。  如果某個資料表變更，您就必須以手動方式更新該資料表的資料錄集，然後重新編譯應用程式。  
  
 您也可以補充精靈產生的程式碼，以處理在編譯時期完全不知道其結構描述的資料庫。  如需詳細資訊，請參閱[資料錄集：動態地繫結資料行 \(ODBC\)](../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。  
  
## 請參閱  
 [Data Access Programming \(MFC\/ATL\)](../data/data-access-programming-mfc-atl.md)   
 [SQL](../data/odbc/sql.md)   
 [資料錄集 \(ODBC\)](../data/odbc/recordset-odbc.md)