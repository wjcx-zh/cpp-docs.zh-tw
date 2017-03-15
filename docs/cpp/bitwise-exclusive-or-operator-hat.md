---
title: "位元互斥 OR 運算子：^ | Microsoft Docs"
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
  - "^ 運算子"
  - "位元運算子, OR 運算子"
  - "互斥 OR 運算子"
  - "運算子 [C++], 位元"
  - "運算子 [C++], 邏輯的"
  - "OR 運算子, 位元互斥"
  - "XOR 運算子"
ms.assetid: f9185d85-65d5-4f64-a6d6-679758d52217
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 位元互斥 OR 運算子：^
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
expression ^ expression  
```  
  
## 備註  
 位元互斥 OR 運算子 \(**^**\) 會比較其第一個運算元的每個位元與第二個運算元的對應位元。  如果其中一個位元為 0，而另一個位元為 1，則會將對應的結果位元設為 1。  否則，對應結果位元會設為 0。  
  
 位元互斥 OR 運算子的兩個運算元都必須為整數類資料類型。  [算術轉換](../misc/arithmetic-conversions.md)中涵蓋的一般算術轉換適用於這些運算元。  
  
## ^ 的運算子關鍵字  
 **xor** 運算子等於 **^** 的文字。  在程式中存取 **xor** 運算子的方式有兩種：包含標頭檔 `iso646.h`，或是使用 [\/Za](../build/reference/za-ze-disable-language-extensions.md) \(停用語言擴充功能\) 編譯器選項進行編譯。  
  
## 範例  
  
```  
// expre_Bitwise_Exclusive_OR_Operator.cpp  
// compile with: /EHsc  
// Demonstrate bitwise exclusive OR  
#include <iostream>  
using namespace std;  
int main() {  
   unsigned short a = 0x5555;      // pattern 0101 ...  
   unsigned short b = 0xFFFF;      // pattern 1111 ...  
  
   cout  << hex << ( a ^ b ) << endl;   // prints "aaaa" pattern 1010 ...  
}  
```  
  
## 請參閱  
 [C\+\+ 位元運算子](../misc/cpp-bitwise-operators.md)   
 [C\+\+ 運算子](../misc/cpp-operators.md)   
 [C\+\+ 運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [C 位元運算子](../c-language/c-bitwise-operators.md)