---
title: "邏輯 AND 運算子：&amp;&amp; | Microsoft Docs"
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
  - "&&"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "&& 運算子"
  - "AND 運算子"
  - "邏輯 AND 運算子"
ms.assetid: 50cfa664-a8c4-4b31-9bab-2f80d7cd2d1f
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 邏輯 AND 運算子：&amp;&amp;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
  
expression   
&&  
 expression  
  
```  
  
## 備註  
 如果兩個運算元都是 **true**，則邏輯 AND 運算子 \(**&&**\) 會傳回布林值 **true**，否則會傳回 **false**。  運算元會在求值之前隱含轉換成 `bool` 類型，而且結果是 `bool` 類型。  邏輯 AND 具有由左至右的順序關聯性。  
  
 邏輯 AND 運算子的運算元不需要屬於相同類型，不過必須屬於整數類資料類型或指標類型。  運算元通常是關聯或相等運算式。  
  
 第一個運算元會經過完整評估，並且會在所有副作用完成之後，才繼續評估邏輯 AND 運算式。  
  
 只有在第一個運算元判斷值為 true \(非零\) 時，才會評估第二個運算元。  這項評估在邏輯 AND 運算式為 false 時，就可以不必評估第二個運算元。  您可以使用這個最少運算評估來預防 null 指標取值，如下列範例所示：  
  
```  
char *pch = 0;  
...  
(pch) && (*pch = 'a');  
```  
  
 如果 `pch` 是 null \(0\)，則永遠不會評估運算式的右邊。  因此，您無法透過 null 指標來進行指派。  
  
## && 的運算子關鍵字  
 **and** 運算子是 **&&** 的文字對等用法。  有兩種方式可存取您程式中的 **and** 運算子：包含標頭檔 `iso646.h`，或是使用 [\/Za](../build/reference/za-ze-disable-language-extensions.md) \(停用語言擴充功能\) 編譯器選項進行編譯。  
  
## 範例  
  
```  
// expre_Logical_AND_Operator.cpp  
// compile with: /EHsc  
// Demonstrate logical AND  
#include <iostream>  
  
using namespace std;  
  
int main() {  
   int a = 5, b = 10, c = 15;  
   cout  << boolalpha  
         << "The true expression "  
         << "a < b && b < c yields "  
         << (a < b && b < c) << endl  
         << "The false expression "  
         << "a > b && b < c yields "  
         << (a > b && b < c) << endl;  
}  
```  
  
## 請參閱  
 [邏輯運算子](../misc/logical-operators.md)   
 [C\+\+ 運算子](../misc/cpp-operators.md)   
 [C\+\+ 運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [C 邏輯運算子](../c-language/c-logical-operators.md)