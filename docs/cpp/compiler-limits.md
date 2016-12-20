---
title: "編譯器限制 | Microsoft Docs"
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
  - "cl.exe 編譯器, 語言建構的限制"
ms.assetid: f1fa59c6-55b4-414b-80c5-3df72952160d
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 編譯器限制
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C\+\+ 標準會建議各種語言的建構限制。  下列是 Visual C\+\+ 編譯器未實作所建議之限制的案例。  第一個數字是 ISO C\+\+ 11 標準 \(INCITS\/ISO\/IEC 14882\-2011\[2012\], Annex B\) 所建立的限制，第二個數字是 Visual C\+\+ 所實作的限制：  
  
-   複合陳述式、反覆項目控制結構及選取控制結構的巢狀層次 \[C\+\+ 標準：256\] \(Visual C\+\+ 編譯器：視陳述式的巢狀組合而定，但通常介於 100 和 110 之間\)。  
  
-   單一巨集定義中的參數 \[C\+\+ 標準：256\] \(Visual C\+\+ 編譯器：127\)。  
  
-   單一巨集引動過程中的引數 \[C\+\+ 標準：256\] \(Visual C\+\+ 編譯器：127\)。  
  
-   字元字串常值或寬字串常值中的字元 \(串連之後\) \[C\+\+ 標準：65536\] \(Visual C\+\+ 編譯器：65535 個單一位元組字元 \(包括 `null` 結束字元\) 及 32767 個雙位元組字元 \(包括 `null` 結束字元\)。  
  
-   單一 `struct-declaration-list` 中的巢狀類別、結構或等位定義層次 \[C\+\+ 標準：256\] \(Visual C\+\+ 編譯器：16\)。  
  
-   建構函式定義中的成員初始設定式 \[C\+\+ 標準：6144\] \(Visual C\+\+ 編譯器：至少 6144\)。  
  
-   單一識別項的範圍限定性條件 \[C\+\+ 標準：256\] \(Visual C\+\+ 編譯器：127\)。  
  
-   巢狀 `extern` 規格 \[C\+\+ 標準：1024\] \(Visual C\+\+ 編譯器：9 \(全域範圍內的隱含 `extern` 規格不列入計數，如果將全域範圍內的隱含 `extern` 規格列入計數，則為 10\)。  
  
-   樣板宣告中的樣板引數 \[C\+\+ 標準：1024\] \(Visual C\+\+ 編譯器：2046\)。  
  
## 請參閱  
 [非標準行為](../cpp/nonstandard-behavior.md)