---
title: "C++ 運算子、優先順序和順序關聯性 | Microsoft Docs"
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
  - "運算子的順序關聯性"
  - "評估順序"
  - "階層, operator"
  - "多個運算子"
  - "運算子優先順序"
  - "運算子 (C++), 順序關聯性"
  - "運算子 (C++), 階層"
  - "運算子 [C++], 優先順序"
  - "優先順序, 運算子"
ms.assetid: 95c1f0ba-dad8-4034-b039-f79a904f112f
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C++ 運算子、優先順序和順序關聯性
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C\+\+ 語言包含所有 C 運算子，並且新增了數個新的運算子。  運算子指定要對一個或多個運算元執行的評估：  
  
 運算子優先順序指定作業在包含多個運算子的運算式中的順序。  運算子關聯性指定在包含多個有相同優先順序之運算子的運算式中，運算元與其左邊或右邊的運算元群組。  下表顯示 C\+\+ 運算子的優先順序和順序關聯性 \(從最高到最低優先順序\)。  除非以括號明確強制其他關聯性，否則運算子的優先順序數字若相同，其優先順序即相等。  
  
### C\+\+ 運算子的優先順序和順序關聯性  
  
|運算子描述|運算子|  
|-----------|---------|  
|`Group 1 precedence, no associativity`|  
|[範圍解析](../cpp/scope-resolution-operator.md)|`::`|  
|`Group 2 precedence, left to right associativity`|  
|[成員選取 \(物件或指標\)](../cpp/member-access-operators-dot-and.md)|`. or –>`|  
|[陣列註標](../cpp/subscript-operator.md)|`[ ]`|  
|[函式呼叫](../cpp/function-call-operator-parens.md)|`( )`|  
|[後置遞增](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|`++`|  
|[後置遞減](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|`––`|  
|[類型名稱](../cpp/typeid-operator.md)|`typeid( )`|  
|[常數類型轉換](../cpp/const-cast-operator.md)|`const_cast`|  
|[動態類型轉換](../cpp/dynamic-cast-operator.md)|`dynamic_cast`|  
|[重新轉譯的類型轉換](../cpp/reinterpret-cast-operator.md)|`reinterpret_cast`|  
|[靜態類型轉換](../cpp/static-cast-operator.md)|`static_cast`|  
|`Group 3 precedence, right to left associativity`|  
|[物件或類型的大小](../cpp/sizeof-operator.md)|`sizeof`|  
|[前置遞增](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|`++`|  
|[前置遞減](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|`––`|  
|[一補數](../cpp/one-s-complement-operator-tilde.md)|`~`|  
|[邏輯 NOT](../cpp/logical-negation-operator-exclpt.md)|`!`|  
|[一元負運算](../misc/unary-negation-operator.md)|`-`|  
|[一元加號](../cpp/unary-plus-and-negation-operators-plus-and.md)|`+`|  
|[傳址](../cpp/lvalue-reference-declarator-amp.md)|`&`|  
|[間接](../cpp/indirection-operator-star.md)|`*`|  
|[建立物件](../cpp/new-operator-cpp.md)|`new`|  
|[終結物件](../cpp/delete-operator-cpp.md)|`delete`|  
|[Cast](../cpp/cast-operator-parens.md)|`Cast: ()`|  
|`Group 4 precedence, left to right associativity`|  
|[成員指標 \(物件或指標\)](../cpp/pointer-to-member-operators-dot-star-and-star.md)|`.* or –>*`|  
|`Group 5 precedence, left to right associativity`|  
|[乘法](../cpp/multiplicative-operators-and-the-modulus-operator.md)|`*`|  
|[除法](../cpp/multiplicative-operators-and-the-modulus-operator.md)|`/`|  
|[模數](../cpp/multiplicative-operators-and-the-modulus-operator.md)|`%`|  
|`Group 6 precedence, left to right associativity`|  
|[加入](../cpp/additive-operators-plus-and.md)|`+`|  
|[減法](../cpp/additive-operators-plus-and.md)|`–`|  
|`Group 7 precedence, left to right associativity`|  
|[左移](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|`<<`|  
|[右移](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|`>>`|  
|`Group 8 precedence, left to right associativity`|  
|[小於](../cpp/relational-operators-equal-and-equal.md)|`<`|  
|[大於](../cpp/relational-operators-equal-and-equal.md)|`>`|  
|[小於或等於](../cpp/relational-operators-equal-and-equal.md)|`<=`|  
|[大於或等於](../cpp/relational-operators-equal-and-equal.md)|`>=`|  
|`Group 9 precedence, left to right associativity`|  
|[相等](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|`==`|  
|[不等](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|`!=`|  
|`Group 10 precedence left to right associativity`|  
|[位元 AND](../cpp/bitwise-and-operator-amp.md)|`&`|  
|`Group 11 precedence, left to right associativity`|  
|[位元互斥 OR](../cpp/bitwise-exclusive-or-operator-hat.md)|`^`|  
|`Group 12 precedence, left to right associativity`|  
|[位元包含 OR](../cpp/bitwise-inclusive-or-operator-pipe.md)|`&#124;`|  
|`Group 13 precedence, left to right associativity`|  
|[邏輯 AND](../cpp/logical-and-operator-amp-amp.md)|`&&`|  
|`Group 14 precedence, left to right associativity`|  
|[邏輯 OR](../cpp/logical-or-operator-pipe-pipe.md)|`&#124;&#124;`|  
|`Group 15 precedence, right to left associativity`|  
|[條件式](../cpp/conditional-operator-q.md)|`? :`|  
|`Group 16 precedence, right to left associativity`|  
|[指派](../cpp/assignment-operators.md)|`=`|  
|[乘法指派](../cpp/assignment-operators.md)|`*=`|  
|[除法指派](../cpp/assignment-operators.md)|`/=`|  
|[模數指派](../cpp/assignment-operators.md)|`%=`|  
|[加法指派](../cpp/assignment-operators.md)|`+=`|  
|[減法指派](../cpp/assignment-operators.md)|`–=`|  
|[左移指派](../cpp/assignment-operators.md)|`<<=`|  
|[右移指派](../cpp/assignment-operators.md)|`>>=`|  
|[位元 AND 指派](../cpp/assignment-operators.md)|`&=`|  
|[位元包含 OR 指派](../cpp/assignment-operators.md)|`&#124;=`|  
|[位元互斥 OR 指派](../cpp/assignment-operators.md)|`^=`|  
|`Group 17 precedence, right to left associativity`|  
|[擲回運算式](../cpp/try-throw-and-catch-statements-cpp.md)|`throw`|  
|`Group 18 precedence, left to right associativity`|  
|[逗號](../cpp/comma-operator.md)|`,`|  
  
## 請參閱  
 [C\+\+ 運算子](../misc/cpp-operators.md)   
 [運算子多載](../cpp/operator-overloading.md)