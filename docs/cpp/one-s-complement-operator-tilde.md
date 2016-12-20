---
title: "一補數運算子：~ | Microsoft Docs"
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
  - "~"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "~ 運算子, 語法"
  - "位元補充運算子"
  - "compl 運算子"
  - "一補數運算子"
  - "波狀符號 (~) 一補數運算子"
ms.assetid: 4bf81967-34f7-4b4b-aade-fd03d5da0174
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 一補數運算子：~
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
  
~ cast-expression  
```  
  
## 備註  
 一補數運算子 \(`~`\)，有時稱為「位元補數」運算子，它會產生其運算元的位元 1 補數。  也就是說，運算元中是 1 的每個位元，在結果中都是 0。  反之，運算元中是 0 的每個位元，在結果中都是 1。  一補數運算子的運算元必須是整數類資料類型。  
  
## ~ 的運算子關鍵字  
 `compl` 運算子是 `~` 的文字對等用法。  有兩種方式可存取您程式中的 `compl` 運算子：包含標頭檔 `iso646.h`，或是使用 [\/Za](../build/reference/za-ze-disable-language-extensions.md) \(停用語言擴充功能\) 進行編譯。  
  
## 範例  
  
```  
// expre_One_Complement_Operator.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
  
int main () {  
   unsigned short y = 0xFFFF;  
   cout << hex << y << endl;  
   y = ~y;   // Take one's complement  
   cout << hex << y << endl;  
}  
```  
  
 在這個範例中，指派至 `y` 的新值是不帶正負號的值 0xFFFF 或 0x0000 的 1 補數。  
  
 整數運算元上會執行整數提升，且結果類型是運算元提升後的類型。  如需如何執行提升的詳細資訊，請參閱[整數提升](../misc/integral-promotions.md)。  
  
## 請參閱  
 [具有一元運算子的運算式](../cpp/expressions-with-unary-operators.md)   
 [C\+\+ 運算子](../misc/cpp-operators.md)   
 [C\+\+ 運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [一元算術運算子](../c-language/unary-arithmetic-operators.md)