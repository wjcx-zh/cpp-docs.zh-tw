---
title: "後置遞增和遞減運算子：++ 和 -- | Microsoft Docs"
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
  - "--"
  - "++"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "-- 運算子, 後置遞減運算子"
  - "++ 運算子, 後置遞增運算子"
  - "遞減運算子"
  - "遞減運算子, 語法"
  - "遞增運算子, 語法"
  - "成員選取運算子"
  - "運算子 [C++], 後置"
  - "後置運算子"
ms.assetid: 0204d5c8-51b0-4108-b8a1-074c5754d89c
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 後置遞增和遞減運算子：++ 和 --
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
  
      postfix-expression   
      ++  
postfix-expression ––  
```  
  
## 備註  
 C\+\+ 提供前置和後置遞增及遞減運算子，本節只說明後置遞增和遞減運算子。\(如需詳細資訊，請參閱[前置遞增和遞減運算子](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)\)。兩者的不同之處是，在後置標記法中，運算子會出現在 *postfix\-expression* 之後，而在前置標記法中，運算子會出現在 *expression* 之前。下列範例顯示後置遞增運算子：  
  
```  
i++;  
```  
  
 套用後置遞增運算子 \(`++`\) 的作用是運算元的值會增加一個單位的適當類型。  同樣地，套用後置遞減運算子 \(**––**\) 的作用是運算元的值會減少一個單位的適當類型。  
  
 請務必注意，後置遞增或遞減運算式會在運用個別運算子**之前**，先求出運算式的值。  遞增或遞減運算會在求出運算元的值**之後**進行。  此問題只有在較大運算式的內容中進行後置遞增或遞減運算時發生。  
  
 使用後置運算子當做函式的引數時，引數的值在傳遞至函式之前不保證會遞增或遞減。如需詳細資訊，請參閱 C\+\+ 標準中的 1.9.17 一節。  
  
 將後置遞增運算子套用至 **long** 類型的物件陣列指標時，其實是新增四個內部指標表示。  這個行為會導致指標 \(先前參考陣列的第 *n* 個項目\) 參考到第 *n\+1* 個項目。  
  
 後置遞增和後置遞減運算子的運算元必須是算術或指標類型的可修改 \(不是 **const**\) 左值。  這個結果的類型與 *postfix\-expression* 相同，不過它不再是左值。  
  
 在求出運算元的值後並將其設定為 **true** 的情況下，後置遞增運算子的運算元也可能是 `bool` 類型。  後置遞減運算子的運算元不能為 `bool` 類型。  
  
 下列程式碼示範後置遞增運算子：  
  
```  
// expre_Postfix_Increment_and_Decrement_Operators.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
int main() {  
   int i = 10;  
   cout << i++ << endl;  
   cout << i << endl;  
}  
```  
  
 不支援在列舉類型上進行後置遞增和後置遞減運算：  
  
```  
enum Compass { North, South, East, West );  
Compass myCompass;  
for( myCompass = North; myCompass != West; myCompass++ ) // Error  
```  
  
## 請參閱  
 [後置運算式](../cpp/postfix-expressions.md)   
 [C\+\+ 運算子](../misc/cpp-operators.md)   
 [C\+\+ 運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [C 後置遞增和遞減運算子](../c-language/c-postfix-increment-and-decrement-operators.md)