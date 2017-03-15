---
title: "Lvalues 和 Rvalues | Microsoft Docs"
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
  - "左值"
  - "右值"
ms.assetid: a8843344-cccc-40be-b701-b71f7b5cdcaf
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Lvalues 和 Rvalues
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

每個 C\+\+ 運算式不是左值就是右值。  左值是指保存在單一運算式之外的物件。  您可以將左值當做具有名稱的物件。  所有變數都是左值，包括不可修改的 \(`const`\) 變數。  右值是暫存值，不會在使用它的運算式之外保存。  若要更加了解左值和右值之間的差異，請參考下列範例：  
  
```  
// lvalues_and_rvalues1.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
int main()  
{  
   int x = 3 + 4;  
   cout << x << endl;  
}  
```  
  
 在這個範例中，`x` 是左值，因為它會在定義它的運算式之外保存。  `3 + 4` 運算式是右值，因為它會判斷值為暫存值，而且不會在定義它的運算式之外保存。  
  
 下列範例將示範數種正確和不正確的左值和右值用法：  
  
```  
// lvalues_and_rvalues2.cpp  
int main()  
{  
   int i, j, *p;  
  
   // Correct usage: the variable i is an lvalue.  
   i = 7;  
  
   // Incorrect usage: The left operand must be an lvalue (C2106).  
   7 = i; // C2106  
   j * 4 = 7; // C2106  
  
   // Correct usage: the dereferenced pointer is an lvalue.  
   *p = i;   
  
   const int ci = 7;  
   // Incorrect usage: the variable is a non-modifiable lvalue (C3892).  
   ci = 9; // C3892  
  
   // Correct usage: the conditional operator returns an lvalue.  
   ((i < 3) ? i : j) = 7;  
}  
```  
  
> [!NOTE]
>  本主題中的範例將說明運算子未多載時的正確和不正確用法。  藉由多載運算子，您就可以讓像是 `j * 4` 這樣的運算式變成左值。  
  
 當您提到物件參考時，會經常用到「*左值*」\(lvalue\) 和「*右值*」\(rvalue\) 這兩個詞彙。  如需有關參考的詳細資訊，請參閱[左值參考宣告子：&](../cpp/lvalue-reference-declarator-amp.md) 和[右值參考宣告子：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。  
  
## 請參閱  
 [基本概念](../cpp/basic-concepts-cpp.md)   
 [左值參考宣告子：&](../cpp/lvalue-reference-declarator-amp.md)   
 [右值參考宣告子：&&](../cpp/rvalue-reference-declarator-amp-amp.md)