---
title: "邏輯 OR 運算子：|| | Microsoft Docs"
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
  - "||"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "|| 運算子"
  - "邏輯 OR 運算子"
  - "OR 運算子"
  - "OR 運算子, 邏輯的"
ms.assetid: 31837c99-2655-4bf3-8ded-f13b7a9dc533
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 邏輯 OR 運算子：||
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
  
logical-or-expression   
||  
 logical-and-expression  
  
```  
  
## 備註  
 如果兩個運算元中任一個或兩個都是 **true**，則邏輯 OR 運算子 \(`||`\) 會傳回布林值 **true**，否則會傳回 **false**。  運算元會在求值之前隱含轉換成 `bool` 類型，而且結果是 `bool` 類型。  邏輯 OR 具有由左至右的順序關聯性。  
  
 邏輯 OR 運算子的運算元不需要屬於相同類型，不過必須屬於整數類資料類型或指標類型。  運算元通常是關聯或相等運算式。  
  
 第一個運算元會經過完整求值，並且會在所有副作用完成之後，才繼續求出邏輯 OR 運算式的值。  
  
 只有在第一個運算元的判斷值為 false \(0\) 時，才會計算第二個運算元的結果。  這樣在邏輯 OR 運算式為 true 時，就可以不必計算第二個運算元的結果。  
  
```  
printf( "%d" , (x == w || x == y || x == z) );  
```  
  
 在上述範例中，如果 `x` 等於 `w`、`y` 或 `z`，則 `printf` 函式的第二個引數判斷值為 true，並且印出值 1。  否則，它的判斷值為 false，並且印出值 0。  只要其中一項條件的判斷值為 true，求值就會停止。  
  
## &#124;&#124; 的運算子關鍵字  
 **or** 運算子是 `||` 的文字對等用法。  有兩種方式可存取您程式中的 **or** 運算子：包含標頭檔 `iso646.h`，或是使用 [\/Za](../build/reference/za-ze-disable-language-extensions.md) \(停用語言擴充功能\) 編譯器選項進行編譯。  
  
## 範例  
  
```  
// expre_Logical_OR_Operator.cpp  
// compile with: /EHsc  
// Demonstrate logical OR  
#include <iostream>  
using namespace std;  
int main() {  
   int a = 5, b = 10, c = 15;  
   cout  << boolalpha  
         << "The true expression "  
         << "a < b || b > c yields "  
         << (a < b || b > c) << endl  
         << "The false expression "  
         << "a > b || b > c yields "  
         << (a > b || b > c) << endl;  
}  
```  
  
## 請參閱  
 [邏輯運算子](../misc/logical-operators.md)   
 [C\+\+ 運算子](../misc/cpp-operators.md)   
 [C\+\+ 運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [C 邏輯運算子](../c-language/c-logical-operators.md)