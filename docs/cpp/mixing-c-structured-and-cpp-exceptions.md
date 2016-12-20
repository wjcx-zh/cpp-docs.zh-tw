---
title: "混合 C (結構化) 和 C++ 例外狀況 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C++ 例外狀況處理, 混合語言"
  - "catch 關鍵字 [C++], 混合"
  - "例外狀況, 混合 C 和 C++"
  - "結構化例外狀況處理, 混合 C 和 C++"
  - "try-catch 關鍵字 [C++], 混合語言"
ms.assetid: a149154e-36dd-4d1a-980b-efde2a563a56
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 混合 C (結構化) 和 C++ 例外狀況
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果您要撰寫更具可攜性的程式碼，不建議您在 C \+\+ 程式中使用結構化的例外狀況處理。  不過，您有時可能想要使用 **\/EHa** 進行編譯並混用結構化例外狀況和 C\+\+ 原始程式碼，而且需要能夠處理這兩種例外狀況的功能。  由於結構化例外狀況處理常式並未具備物件或具類型之例外狀況的概念，因此無法處理 C\+\+ 程式碼所擲回的例外狀況，不過 C\+\+ **catch** 處理常式可以處理結構化例外狀況。  因此，C 編譯器不接受 C\+\+ 例外狀況處理語法 \(**try**、`throw`、**catch**\)，但是 C\+\+ 編譯器支援結構化例外狀況處理語法 \(`__try`、`__except`、`__finally`\)。  
  
 如需將結構化例外狀況當做 C\+\+ 例外狀況處理的詳細資訊，請參閱 [\_set\_se\_translator](../c-runtime-library/reference/set-se-translator.md)。  
  
 如果您混用結構化和 C\+\+ 例外狀況，請注意下列事項：  
  
1.  C\+\+ 例外狀況和結構化例外狀況無法在同一個函式中混用。  
  
2.  即使是在擲回例外狀況之後的回溯期間，終止處理常式 \(`__finally` 區塊\) 一律會執行。  
  
3.  C\+\+ 例外狀況處理可以攔截並保留使用 [\/EH](../build/reference/eh-exception-handling-model.md) 編譯器選項編譯之所有模組中的回溯語意 \(這個選項會啟用回溯語意\)。  
  
4.  在某些情況下，可能不會針對所有物件呼叫解構函式的函式。  例如，如果嘗試透過未初始化的函式指標進行函式呼叫時發生結構化例外狀況，而且該函式採用呼叫前建構的物件做為參數，則這些物件不會在堆疊回溯期間呼叫其解構函式。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [在 C\+\+ 程式中使用 setjmp 或 longjmp](../cpp/using-setjmp-longjmp.md)  
  
-   [SEH 與 C\+\+ EH 的差異](../cpp/exception-handling-differences.md)  
  
## 請參閱  
 [C\+\+ 例外狀況處理](../cpp/cpp-exception-handling.md)