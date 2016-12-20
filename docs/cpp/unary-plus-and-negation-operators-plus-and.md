---
title: "一元正和負運算子：+ 和 - | Microsoft Docs"
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
  - "+"
  - "-"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "- 運算子"
  - "+ 運算子"
  - "+ 運算子, 一元運算子"
  - "negation 運算子"
  - "一元運算子, plus"
ms.assetid: 2c58c4f4-0d92-4ae3-9d0c-1a6157875cc1
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 一元正和負運算子：+ 和 -
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
  
+ cast-expression  
```  
  
```  
  
- cast-expression  
  
```  
  
## \+ 運算子  
 一元加法運算子 \(**\+**\) 的結果是其運算元的值。  一元加法運算子的運算元必須屬於算術類型。  
  
 整數提升會在整數運算元上執行。  結果類型會是運算元提升後的類型。  因此，運算式 `+ch` \(其中 `ch` 的類型為 `char`\) 會得到 `int` 類型，且值未經修改。  如需如何執行提升的詳細資訊，請參閱[整數提升](../misc/integral-promotions.md)。  
  
## \- 運算子  
 一元負運算子 \(**–**\) 會產生其運算元的負數。  一元負運算子的運算元必須是算術類型。  
  
 整數運算元上會執行整數提升，且結果類型是運算元提升後的類型。  如需如何執行提升的詳細資訊，請參閱[整數提升](../misc/integral-promotions.md)。  
  
## Microsoft 專有的  
 不帶正負號數量的一元否定執行方式是 2^n 減去運算元的值，其中 n 是指定不帶正負號類型之物件的位元數   \(Microsoft C\+\+ 執行於運用二補數算術的處理器。  在其他處理器上，否定的演算法可能不同\)。  
  
## 請參閱  
 [具有一元運算子的運算式](../cpp/expressions-with-unary-operators.md)   
 [C\+\+ 運算子](../misc/cpp-operators.md)   
 [C\+\+ 運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)