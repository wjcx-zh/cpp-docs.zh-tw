---
title: "位元 AND 運算子：&amp; | Microsoft Docs"
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
  - "bitand"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "& 運算子, 位元運算子"
  - "AND 運算子"
  - "位元運算子, AND 運算子"
ms.assetid: 76f40de3-c417-47b9-8a77-532f3fc990a5
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 位元 AND 運算子：&amp;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
  
expression   
&  
 expression  
  
```  
  
## 備註  
 運算式可以是其他 and 運算式或 \(受限於如下所述的限制\) 相等的運算式、關聯運算式，加法運算式、乘法運算式、成員運算式的指標、cast 運算式、一元運算式、後置運算式或主要運算式。  
  
 位元 AND 運算子 \(**&**\) 會比較第一個運算元的每個位元，以及第二個運算元的對應位元。  如果兩個位元皆為 1，則對應的結果位元會設為 1。  否則，對應結果位元會設為 0。  
  
 位元 AND 運算子的兩個運算元都必須為整數類型。  [算術轉換](../misc/arithmetic-conversions.md)中涵蓋的一般算術轉換適用於這些運算元。  
  
## & 的運算子關鍵字  
 `bitand` 運算子是 **&** 的文字對等用法。  有兩種方式可存取您程式中的 `bitand` 運算子：包含標頭檔 `iso646.h`，或是使用 [\/Za](../build/reference/za-ze-disable-language-extensions.md) \(停用語言擴充功能\) 編譯器選項進行編譯。  
  
## 範例  
  
```  
// expre_Bitwise_AND_Operator.cpp  
// compile with: /EHsc  
// Demonstrate bitwise AND  
#include <iostream>  
using namespace std;  
int main() {  
   unsigned short a = 0xFFFF;      // pattern 1111 ...  
   unsigned short b = 0xAAAA;      // pattern 1010 ...  
  
   cout  << hex << ( a & b ) << endl;   // prints "aaaa", pattern 1010 ...  
}  
```  
  
## 請參閱  
 [C\+\+ 位元運算子](../misc/cpp-bitwise-operators.md)   
 [C\+\+ 運算子](../misc/cpp-operators.md)   
 [C\+\+ 運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [C 位元運算子](../c-language/c-bitwise-operators.md)