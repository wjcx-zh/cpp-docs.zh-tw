---
title: "成員存取運算子：. 和 -&gt; | Microsoft Docs"
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
  - "."
  - "->"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ". 運算子"
  - "-> 運算子"
  - "點 (.) 運算子"
  - "成員存取"
  - "成員存取, 運算式"
  - "成員存取, 運算子"
  - "運算子 [C++], 成員存取"
  - "後置運算子"
ms.assetid: f8fc3df9-d728-40c5-b384-276927f5f1b3
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 成員存取運算子：. 和 -&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
  
      postfix-expression   
      . name  
postfix-expression –> name  
```  
  
## 備註  
 成員存取運算子 **.** 和 **\-\>** 是用來參考結構、等位和類別的成員。  成員存取運算式具有選定成員的值和類型。  
  
 成員存取運算式有兩種形式：  
  
1.  在第一種形式中，*postfix\-expression* 代表結構、類別或等位類型的值，而 *name* 則會為指定結構、等位或類別的成員命名。  運算式的值會是 *name* 的值，而且如果 *postfix\-expression* 為左值，運算式的值也會是左值。  
  
2.  在第二種形式中，*postfix\-expression* 代表結構、等位或類別的指標，而 *name* 會為指定結構、等位或類別的成員命名。  值會是 *name* 的值，而且是左值。  **–\>** 運算子會取值指標。  因此，運算式 *e***–\>**`member` 和 **\(\****e***\)**.`member` \(其中 *e* 代表指標\) 會產生相同的結果 \(但運算子 **–\>** 或 **\*** 多載時除外\)。  
  
## 範例  
 下列範例示範成員存取運算子的兩種形式。  
  
```  
// expre_Selection_Operator.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
struct Date {  
   Date(int i, int j, int k) : day(i), month(j), year(k){}  
   int month;  
   int day;  
   int year;  
};  
  
int main() {  
   Date mydate(1,1,1900);  
   mydate.month = 2;     
   cout  << mydate.month << "/" << mydate.day  
         << "/" << mydate.year << endl;  
  
   Date *mydate2 = new Date(1,1,2000);  
   mydate2->month = 2;  
   cout  << mydate2->month << "/" << mydate2->day  
         << "/" << mydate2->year << endl;  
   delete mydate2;  
}  
```  
  
  **2\/1\/1900**  
**2\/1\/2000**   
## 請參閱  
 [後置運算式](../cpp/postfix-expressions.md)   
 [C\+\+ 運算子](../misc/cpp-operators.md)   
 [C\+\+ 運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [類別和結構](../cpp/classes-and-structs-cpp.md)   
 [結構和等位成員](../c-language/structure-and-union-members.md)