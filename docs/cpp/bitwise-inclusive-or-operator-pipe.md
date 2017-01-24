---
title: "位元非互斥 OR 運算子：| | Microsoft Docs"
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
  - "bitor"
  - "|"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "| 運算子"
  - "位元運算子, OR 運算子"
  - "非互斥 OR 運算子"
  - "OR 運算子, 位元非互斥"
ms.assetid: 4c8a6a68-d828-447d-875a-aedb4ce3aa9a
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 位元非互斥 OR 運算子：|
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
  
expression   
|  
 expression  
  
```  
  
## 備註  
 位元包含 OR 運算子 \(         **&#124;** \) 會比較其第一個運算元的每個位元，以及第二個運算元的對應位元。  如果任一位元為 1，則對應結果位元會設為 1。  否則，對應結果位元會設為 0。  
  
 位元包含 OR 運算子的兩個運算元都必須為整數類資料類型。  [算術轉換](../misc/arithmetic-conversions.md)中涵蓋的一般算術轉換適用於這些運算元。  
  
## &#124; 的運算子關鍵字  
 `bitor` 運算子是下列運算子的文字對等用法：             **&#124;** .  有兩種方式可存取您程式中的 `bitor` 運算子：包含標頭檔 `iso646.h`，或是使用 [\/Za](../build/reference/za-ze-disable-language-extensions.md) \(停用語言擴充功能\) 編譯器選項進行編譯。  
  
## 範例  
  
```  
// expre_Bitwise_Inclusive_OR_Operator.cpp  
// compile with: /EHsc  
// Demonstrate bitwise inclusive OR  
#include <iostream>  
using namespace std;  
  
int main() {  
   unsigned short a = 0x5555;      // pattern 0101 ...  
   unsigned short b = 0xAAAA;      // pattern 1010 ...  
  
   cout  << hex << ( a | b ) << endl;   // prints "ffff" pattern 1111 ...  
}  
```  
  
## 請參閱  
 [C\+\+ 位元運算子](../misc/cpp-bitwise-operators.md)   
 [C\+\+ 運算子](../misc/cpp-operators.md)   
 [C\+\+ 運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [C 位元運算子](../c-language/c-bitwise-operators.md)