---
title: "C++ 程式啟動和終止 | Microsoft Docs"
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
  - "控制文字資料流"
  - "函式 Main 程序"
  - "main 函式, 程式啟動"
  - "Standard C++ 程式庫, 程式啟動和終止"
  - "啟始程式碼, 和 C++ 程式終止"
  - "終止執行"
ms.assetid: f72c8f76-f507-4ddd-a270-7b60f4fed625
caps.latest.revision: 9
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# C++ 程式啟動和終止
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C \+\+. 程式執行相同 C\+\+. 程式在程式啟動且程式終止作業，加上外框陣列這裡。  
  
 在目標環境函式呼叫 `main`之前，因此，，會儲存所有常數值之後在有靜態期間的所有物件，程式執行這類靜態物件的其他建構函式。  執行的順序未指定在轉譯單位之間，然而，但是您可以假設，某些 [iostreams](../standard-library/iostreams-conventions.md) 物件正確初始化供這些靜態建構函式。  這些控制項的文字資料流是:  
  
-   [cin](../Topic/cin.md) —標準輸入的。  
  
-   [cout](../Topic/cout.md) —標準輸出的。  
  
-   [cerr](../Topic/cerr.md) —無緩衝區的標準錯誤輸出的。  
  
-   [阻礙。](../Topic/clog.md) —緩衝區的標準錯誤輸出的。  
  
 您可以為靜態物件可以使用在程式結束時呼叫的，解構函式內的這些物件。  
  
 與 C，傳回 `main` 或 `exit` 呼叫的所有函式向註冊反向的 `atexit` 。  從所擲回的例外狀況註冊的函式呼叫 `terminate`。  
  
## 請參閱  
 [STL 概觀](../standard-library/cpp-standard-library-overview.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)