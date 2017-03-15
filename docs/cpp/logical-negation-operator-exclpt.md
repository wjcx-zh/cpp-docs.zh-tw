---
title: "邏輯負運算子：! | Microsoft Docs"
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
  - "!"
  - "Not"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "! 運算子"
  - "邏輯否定"
  - "NOT 運算子"
ms.assetid: 650add9f-a7bc-426c-b01d-5fc6a81c8b62
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 邏輯負運算子：!
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
  
! cast-expression  
```  
  
## 備註  
 邏輯負運算子 \(**\!**\) 會反轉其運算元的意義。  運算元必須是算術或指標類型 \(或判斷值為算術或指標類型的運算式\)。  運算元會隱含轉換成 `bool` 類型。  如果轉換的運算元為 **false**，則結果是 **true**，如果轉換的運算元為 **true**，則結果會是 **false**。  其結果會是 `bool` 類型。  
  
 對於運算式 *e*，一元運算式 **\!***e* 等同於運算式 **\(***e* `==` 0\)，不同的是其中會包含多載的運算子。  
  
## \! 的運算子關鍵字  
 **not** 運算子是 **\!** 的文字對等用法。  有兩種方式可存取您程式中的 **not** 運算子：包含標頭檔 `iso646.h`，或是使用 [\/Za](../build/reference/za-ze-disable-language-extensions.md) \(停用語言擴充功能\) 編譯器選項進行編譯。  
  
## 範例  
  
```  
// expre_Logical_NOT_Operator.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
int main() {  
   int i = 0;  
   if (!i)  
      cout << "i is zero" << endl;  
}  
```  
  
## 請參閱  
 [具有一元運算子的運算式](../cpp/expressions-with-unary-operators.md)   
 [C\+\+ 運算子](../misc/cpp-operators.md)   
 [C\+\+ 運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [一元算術運算子](../c-language/unary-arithmetic-operators.md)