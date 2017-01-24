---
title: "&lt;iostream&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.<iostream>"
  - "std::<iostream>"
  - "<iostream>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "iostream 標頭"
ms.assetid: de5d39e1-7e77-4b55-bcd1-7c77b41515c8
caps.latest.revision: 23
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;iostream&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

宣告對標準資料流的讀取和寫入進行控制的物件。  這通常是您從 C\+\+ 程式中執行輸入和輸出時唯一需要納入的標頭。  
  
## 語法  
  
```  
  
#include <iostream>  
  
```  
  
## 備註  
 這些物件可分為兩個群組：  
  
-   [cin](../Topic/cin.md)、[cout](../Topic/cout.md)、[cerr](../Topic/cerr.md) 和 [clog](../Topic/clog.md) 屬於位元組導向，執行傳統以位元組為單位的傳輸。  
  
-   [wcin](../Topic/wcin.md)、[wcout](../Topic/wcout.md)、[wcerr](../Topic/wcerr.md) 和 [wclog](../Topic/wclog.md) 屬於全方向導向，會對程式內部操作的寬字元進行雙向轉譯。  
  
 在您對資料流執行特定作業後 \(例如標準輸入\)，您無法對相同的資料流執行不同方向的作業。  因此，舉例來說，程式無法對 [cin](../Topic/cin.md) 和 [wcin](../Topic/wcin.md) 執行可互換的作業。  
  
 在此標頭中宣告的所有物件會共用特定屬性 — 您可以假設這些物件是在包含 \<iostream\> 的轉譯單位中所定義的任何靜態物件之前建構的。  同樣地，您可以假設這類物件不會在您定義的任何此類靜態物件的解構函式之前終結。  \(但輸出資料流會在程式終止期間排清。\) 因此，在程式啟動之前和程式終止之後，您可以安全地讀取或寫入標準資料流。  
  
 但這項保證並非一體適用。  靜態建構函式可能會在另一個轉譯單位中呼叫函式。  由於轉譯單位參與靜態建構的順序並不確定，呼叫的函式無法假設在此標頭中宣告的物件已建構。  若要在這類內容中使用這些物件，您必須先建構類別 [ios\_base::init](../Topic/ios_base::Init.md) 的物件。  
  
### 全域資料流物件  
  
|||  
|-|-|  
|[cerr](../Topic/cerr.md)|指定 `cerr` 全域資料流。|  
|[cin](../Topic/cin.md)|指定 `cin` 全域資料流。|  
|[clog](../Topic/clog.md)|指定 `clog` 全域資料流。|  
|[cout](../Topic/cout.md)|指定 `cout` 全域資料流。|  
|[wcerr](../Topic/wcerr.md)|指定 `wcerr` 全域資料流。|  
|[wcin](../Topic/wcin.md)|指定 `wcin` 全域資料流。|  
|[wclog](../Topic/wclog.md)|指定 `wclog` 全域資料流。|  
|[wcout](../Topic/wcout.md)|指定 `wcout` 全域資料流。|  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 程式設計](../standard-library/iostream-programming.md)   
 [iostreams 慣例](../standard-library/iostreams-conventions.md)