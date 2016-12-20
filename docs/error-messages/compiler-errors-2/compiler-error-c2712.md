---
title: "編譯器錯誤 C2712 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2712"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2712"
ms.assetid: f7d4ffcc-7ed2-459b-8067-a728ce647071
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2712
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法在需要物件回溯 \(Object Unwinding\) 的函式中使用 \_\_try  
  
 如果您使用 [\/EHsc](../../build/reference/eh-exception-handling-model.md)，且具有結構化例外狀況處理的函式也有需要回溯 \(解構\) 的物件，就可能發生錯誤 C2712。  
  
 可能的解決方案：  
  
-   將需要 SEH 的程式碼移至另一個函式  
  
-   重寫使用 SEH 的函式，以避免使用具有解構函式的本機變數和參數。  請勿在建構函式或解構函式中使用 SEH  
  
-   編譯時不要使用 \/EHsc  
  
 如果您呼叫以 [\_\_event](../../cpp/event.md) 關鍵字宣告的方法，也會發生錯誤 C2712。  由於事件可能會用在多執行緒環境中，因此編譯器會產生程式碼以防止基礎事件物件的操作，然後將產生的程式碼包含在 SEH [try\-finally 陳述式](../../cpp/try-finally-statement.md)中。  因此，如果您呼叫事件方法，並以類型具有解構函式的引數傳值，就會發生錯誤 C2712。  此情況下的解決方案之一，是傳遞引數做為常數參考。  
  
## 範例  
 如果您使用 **\/clr:pure** 進行編譯，並在 `__try` 區塊中宣告指標對函式的靜態陣列，也可能會發生 C2712。  靜態成員需要有編譯器才能在 **\/clr:pure** 下使用動態初始化，而這意味著 C\+\+ 例外狀況處理。  然而，在 `__try` 區塊中不允許執行 C\+\+ 例外狀況處理。  
  
 下列範例會產生 C2712，並說明如何加以修正。  
  
```  
// C2712.cpp  
// compile with: /clr:pure /c  
struct S1 {  
   static int smf();  
   void fnc();  
};  
  
void S1::fnc() {  
   __try {  
      static int (*array_1[])() = {smf,};   // C2712  
  
      // OK  
      static int (*array_2[2])();  
      array_2[0] = smf;  
    }  
    __except(0) {}  
}  
```