---
title: "關係運算子：&lt;、&gt;、&lt;= 和 &gt;= | Microsoft Docs"
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
  - "<"
  - ">"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "< 運算子"
  - "<= 運算子"
  - "> 運算子"
  - ">= 運算子"
  - "大於運算子"
  - "大於或等於運算子"
  - "小於運算子"
  - "小於或等於運算子"
  - "關係運算子, 語法"
ms.assetid: d346b53d-f14d-4962-984f-89d39a17ca0f
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 關係運算子：&lt;、&gt;、&lt;= 和 &gt;=
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
  
        expression < expression  
expression > expression  
expression <= expression  
expression >= expression  
```  
  
## 備註  
 二元關係運算子決定下列關聯性：  
  
-   小於 \(**\<**\)  
  
-   大於 \(**\>**\)  
  
-   小於或等於 \(**\<\=**\)  
  
-   大於或等於 \(**\>\=**\)  
  
 關係運算子具有由左到右的順序關聯性。  關係運算子的兩個運算元都必須是算術或指標類型。  這些類型會產生 `bool` 類型的值。  如果運算式中的關聯性是 false，傳回的值會是 **false** \(0\)；否則，傳回的值會是 **true** \(1\)。  
  
## 範例  
  
```  
// expre_Relational_Operators.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
  
int main() {  
   cout  << "The true expression 3 > 2 yields: "  
         << (3 > 2) << endl  
         << "The false expression 20 < 10 yields: "  
         << (20 < 10) << endl;  
}  
```  
  
 上述範例中的運算式必須以括號括住，因為資料流插入運算子 \(**\<\<**\) 的優先順序高於關係運算子。  因此，不加括弧的第一個運算式會評估為：  
  
```  
(cout << "The true expression 3 > 2 yields: " << 3) < (2 << "\n");  
```  
  
 [算術轉換](../misc/arithmetic-conversions.md)中的一般算術轉換適用於算術類型的運算元。  
  
## 比較指標  
 比較相同類型的兩個物件指標時，結果是取決於程式的位址空間中所指向的物件位置。  指標也可以與判斷值為 0 的常數運算式或 void \* 類型的指標進行比較。  如果是對 void \* 類型的指標進行指標比較，則另一個指標會先隱含轉換成 void \* 類型，  然後才進行比較。  
  
 兩個不同類型的指標無法進行比較，除非：  
  
-   其中一個類型是衍生自另一個類型的類別類型。  
  
-   至少有一個指標已明確轉換 \(轉型\) 為 void \* 類型   \(另一個指標會隱含轉換成 void \* 類型以便進行轉換\)。  
  
 相同類型且指向相同物件之兩個指標的比較結果一定為相等。  如果將物件的兩個非靜態成員指標相互比較，則適用下列規則：  
  
-   如果類別類型不是等位，而且未以 *access\-specifier* \(例如 public、protected 或 private\) 分隔兩個成員，則最後宣告的成員指標比較結果會大於之前宣告的成員指標   \(如需 *access\-specifier* 的詳細資訊，請參閱[存取指定名稱](../misc/access-specifiers.md)中的＜語法＞一節\)。  
  
-   如果以 *access\-specifier* 分隔兩個成員，則結果會是未定義。  
  
-   如果類別類型是等位，則該等位中不同資料成員的指標比較結果為相等。  
  
 如果兩個指標指向相同陣列的元素，或指向超出陣列結尾的元素一，則具有較高註標的物件指標比較結果會較高。  只有在指標參考相同陣列中的物件或超出陣列結尾的位置一時，才能保證指標比較有效。  
  
## 請參閱  
 [具有二元運算子的運算式](../cpp/expressions-with-binary-operators.md)   
 [C\+\+ 運算子](../misc/cpp-operators.md)   
 [C\+\+ 運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [C 關係和等號比較運算子](../c-language/c-relational-and-equality-operators.md)