---
title: "C++ 註解 | Microsoft Docs"
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
  - "程式碼註解, C++"
  - "註解, C++ 程式碼"
  - "註解, 撰寫程式碼"
  - "空白字元, C++ 註解"
ms.assetid: 6fcb906c-c264-4083-84bc-373800b2e514
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C++ 註解
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

註解是會被編譯器忽略的文字，但對程式設計人員而言很有用。  註解通常用來註解程式碼供未來參考。  編譯器會將它們視為空白字元。  您可以在測試中使用註解讓特定的程式碼無法作用；不過， `#if`\/`#endif` 前置處理器指示詞可以更好運作，因為您可以放在包含註解的程式碼外圍，但是您無法巢狀註解。  
  
 C \+\+ 是註解以下列其中一種方式撰寫；  
  
-   `/*` \(斜線，星號\) 字元，後面接著任何字元序列 \(包括新行\)，後面接著 `*/` 字元。  這語法與 ANSI C 相同。  
  
-   `//` \(兩個斜線\) 字元，後面接著任何字元序列。  一個沒有前置反斜線的新行會終止這種形式的註解。  因此，它通常稱為「單行註解」。  
  
 註解字元 \(`/*`、 `*/`和 `//`\) 在字元常數、字串常值、註解中沒有特殊意義。  因此，使用第一種語法的註解不可以是巢狀。  
  
## 請參閱  
 [語彙慣例](../cpp/lexical-conventions.md)