---
title: "bool (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "bool_cpp"
  - "bool"
  - "__BOOL_DEFINED"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__BOOL_DEFINED 巨集"
  - "bool 關鍵字 [C++]"
ms.assetid: 9abed3f2-d21c-4eb4-97c5-716342e613d8
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# bool (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這個關鍵字是內建類型。  這個類型變數的值可以是 [true](../cpp/true-cpp.md) 和 [false](../cpp/false-cpp.md)。  條件運算式具有 `bool` 類型，因此具有 `bool` 類型的值。  例如，根據 `i` 的值而定，`i!=0` 現在會有 **true** 或 **false**。  
  
 **true** 和 **false** 值具有下列關聯性：  
  
```  
!false == true  
!true == false  
```  
  
 在下列陳述式中：  
  
```  
if (condexpr1) statement1;   
```  
  
 如果 `condexpr1` 是 **true**，則 `statement1` 一定會執行，如果 `condexpr1` 是 **false**，則 `statement1` 絕不會執行。  
  
 當前置或後置 `++` 運算子套用至 `bool` 類型的變數時，變數會設定為 **true**。  後置或前置 `--` 運算子不可套用至這種類型的變數。  
  
 `bool` 類型會參與整數提升。  `bool` 類型的右值可以轉換成 `int` 類型的右值，同時 **false** 會變成零且 **true** 會變成一。  `bool` 為不同類型，它會參與多載解析。  
  
## 請參閱  
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)   
 [基本類型](../cpp/fundamental-types-cpp.md)