---
title: "輸入/輸出替代項目 | Microsoft Docs"
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
  - "I/O [C++], 替代項目"
ms.assetid: 9f8401c7-d90d-4285-8918-63573df74a80
caps.latest.revision: 8
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 輸入/輸出替代項目
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 的 I\/O 程式設計提供數個選項:  
  
-   C 執行階段程式庫直接，無緩衝區的 I\/O。  
  
-   ANSI C 執行階段程式庫資料流 I\/O。  
  
-   主控台和連接埠直接 I\/O。  
  
-   MFC 程式庫。  
  
-   Microsoft Standard C\+\+ 程式庫。  
  
 從類別為緩衝區很有用，格式化 I\/O。  如果您需要 C \+\+. 程式設計介面並選擇不使用 Microsoft Foundation Class \(MFC\) 程式庫，其為無緩衝區或二進位 I\/O 也很有用。  從類別是物件導向的 I\/O 替代 C 執行階段函式。  
  
 您可以使用與作業系統的 Windows 的 iostream 類別。  字串和檔案資料流運作沒有限制，不過，字元模式資料流物件的 `cin`、 `cout`、 `cerr`和 `clog` 與 Windows 圖形化使用者介面不一致。  您也可以取得直接與 Windows 環境互動的自訂資料流類別。  
  
## 請參閱  
 [什麼是資料流](../standard-library/what-a-stream-is.md)