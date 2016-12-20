---
title: "C 常數運算式 | Microsoft Docs"
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
  - "C"
helpviewer_keywords: 
  - "常數運算式"
  - "常數運算式, 語法"
  - "運算式 [C++], 常數"
ms.assetid: d48a6c47-e44c-4be2-9c8b-7944c7ef8de7
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C 常數運算式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

常數運算式會在編譯時期評估，而不是在執行階段評估，而且可用於可以使用常數的任何位置。  常數運算式必須評估為常數，並且必須在該類型可顯示值的範圍內。  常數運算式的運算元可以是整數常數、字元常數、浮點常數、列舉常數、類型轉換、`sizeof` 運算式和其他常數運算式。  
  
## 語法  
 *constant\-expression*:  
 *條件運算式*  
  
 *conditional\-expression*:  
 *logical\-OR\-expression*  
  
 *logical\-OR\-expression* **?**  *expression* **:**  *conditional\-expression*  
  
 *expression*：  
 *assignment\-expression*  
  
 *expression* **,**  *assignment\-expression*  
  
 *assignment\-expression*：  
 *條件運算式*  
  
 *一元運算式指派運算子指派運算式*  
  
 *assignment\-operator*：其中一項  
 **\= \*\= \/\= %\= \+\= –\= \<\<\= \>\>\= &\= ^\= &#124;\=**  
  
 結構宣告子、列舉程式、直接宣告子、直接抽象宣告子和標記陳述式包含 *constant\-expression* 非終端項。  
  
 必須使用整數常數運算式指定結構的位元欄位成員、列舉常數的值、陣列的大小或「大小寫」常數的值。  
  
 前置處理器指示詞中所使用的常數運算式必須遵守其他限制。  因此，這些運算式稱為「受限制的常數運算式」。受限制的常數運算式不能包含 `sizeof` 運算式、列舉常數、任何類型的類型轉換，或浮點類型常數。  不過，此類運算式可以包含特殊常數運算式 `defined (`*identifier*`)`。  
  
## 請參閱  
 [運算元和運算式](../c-language/operands-and-expressions.md)