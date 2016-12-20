---
title: "編譯器錯誤 C2558 | Microsoft Docs"
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
  - "C2558"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2558"
ms.assetid: 822b701e-dcae-423a-b21f-47f36aff9c90
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2558
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 沒有可用的複製建構函式或是複製建構函式宣告為 'explicit'  
  
 複製建構函式 \(Copy Constructor\) 從另一個相同類型的物件上初始化物件   \(它產生一個物件的複本\)。如果您未定義任何建構函式，則編譯器會產生一個預設複製建構函式。  
  
### 若要修正這個錯誤  
  
1.  當嘗試複製的類別所擁有的複製建構函式為 `private` 時，就可能會發生這個問題。  在大部分情況下，不應複製具有 `private` 複製建構函式的類別。  一般程式設計技術會宣告一個 `private` 複製建構函式，來防止直接使用類別。  該類別單獨使用可能毫無用處，或需要另一個類別才能正確運作。  
  
     如果您判斷使用具有 `private` 複製建構函式的類別是安全的，則從具有 `private` 建構函式的類別上衍生新的類別，並在新類別中提供 `public` 或 `protected` 複製建構函式使用。  使用這個衍生類別取代原本的。  
  
2.  當嘗試複製的類別擁有明確的複製建構函式時，可能會發生這個問題。  將複製建構函式宣告為 `explicit`，可防止將類別的物件傳遞至函式，或將類別的物件從函式傳回。  如需明確建構函式的相關資訊，請參閱[轉換](../../cpp/user-defined-type-conversions-cpp.md)。  
  
3.  若嘗試複製的類別執行個體使用複製建構函式宣告了 `const`，但該建構函式未採用 `const` 傳址參數，就可能會發生這個問題。  請宣告具有 `const` 類型參考而不是非常數類型參考的複製建構函式。