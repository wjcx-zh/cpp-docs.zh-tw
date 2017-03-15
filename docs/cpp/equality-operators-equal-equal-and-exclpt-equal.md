---
title: "等號比較運算子：== 和 != | Microsoft Docs"
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
  - "not_eq"
  - "!="
  - "=="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "!= 運算子"
  - "== 運算子"
  - "等於運算子"
  - "等號比較運算子"
  - "等號比較運算子, 語法"
  - "不等於比較運算子"
  - "not_eq 運算子"
ms.assetid: ba4e9659-2392-4fb4-be5a-910a2a6df45a
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 等號比較運算子：== 和 !=
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
  
      expression == expression  
expression != expression  
```  
  
## 備註  
 二進位相等運算子會比較其運算元，以進行嚴格的相等或不等比較。  
  
 相等運算子等於 \(`==`\) 和不等於 \(`!=`\) 的優先順序低於關係運算子，但是它們的行為類似。  這些運算子的結果類型為 `bool`。  
  
 如果兩個運算元具有相同的值，則等於運算子 \(`==`\) 會傳回 **true** \(1\)，否則會傳回 **false** \(0\)。  如果運算元的值不相同，則不等於運算子 \(`!=`\) 會傳回 **true**，否則會傳回 **false**。  
  
## \!\= 的運算子關鍵字  
 `not_eq` 運算子是 `!=` 的文字對等用法。  有兩種方式可存取您程式中的 `not_eq` 運算子：包含標頭檔 `iso646.h`，或是使用 [\/Za](../build/reference/za-ze-disable-language-extensions.md) \(停用語言擴充功能\) 編譯器選項進行編譯。  
  
## 範例  
  
```  
// expre_Equality_Operators.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
  
int main() {  
   cout  << boolalpha  
         << "The true expression 3 != 2 yields: "  
         << (3 != 2) << endl  
         << "The false expression 20 == 10 yields: "  
         << (20 == 10) << endl;  
}  
```  
  
 相等運算子可以比較相同類型成員的指標。  這類比較會執行成員指標轉換，如[成員指標轉換](../misc/pointer-to-member-conversions.md)中所討論。  成員指標也可以與判斷值為 0 的常數運算式進行比較。  
  
## 請參閱  
 [具有二元運算子的運算式](../cpp/expressions-with-binary-operators.md)   
 [C\+\+ 運算子](../misc/cpp-operators.md)   
 [C\+\+ 運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [C 關係和等號比較運算子](../c-language/c-relational-and-equality-operators.md)