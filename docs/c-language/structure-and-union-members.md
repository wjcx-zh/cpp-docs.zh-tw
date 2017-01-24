---
title: "結構和等位成員 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - ". 運算子"
  - "-> 運算子, 結構和等位成員"
  - "點 (.) 運算子"
  - "成員選取運算子"
  - "運算子 [C], 成員選取"
  - "參考結構成員"
  - "制結構成員選取"
  - "結構成員, 參考"
ms.assetid: bb1fe304-af49-4f98-808d-afdc99b3e319
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 結構和等位成員
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

「成員選取運算式」\(Member\-selection Expression\) 會參考結構和等位的成員。  這類運算式具有所選取成員的值和類型。  
  
```  
  
        postfix-expression . identifier  
postfix-expression –> identifier  
```  
  
 這個清單將描述兩種形式的成員選取運算式：  
  
1.  在第一種形式中，*postfix\-expression* 代表 `struct` 或 **union** 類型的值，而 *identifier* 會為所指定結構或等位的成員命名。  運算的值會是 *identifier* 的值，而且如果 *postfix\-expression* 為左值，運算的值也會是左值。  如需詳細資訊，請參閱[左值和右值運算式](../c-language/l-value-and-r-value-expressions.md)。  
  
2.  在第二種形式中，*postfix\-expression* 代表結構或等位的指標，而 *identifier* 會為所指定結構或等位的成員命名。  值會是 *identifier* 的值，而且是左值。  
  
 這兩種形式的成員選取運算式會產生類似的效果。  
  
 實際上，如果句號前的運算式是由套用至指標值的間接取值運算子 \(**\***\) 所組成，則包含成員選取運算子 \(**–\>**\) 的運算式會是使用句號 \(**.**\) 之運算式的簡短版。  因此，  
  
```  
  
expression –> identifier  
```  
  
 相當於  
  
```  
  
(*  
expression  
) . identifier  
```  
  
 \(*expression* 為指標值時\)。  
  
## 範例  
 下列範例會參考這個結構宣告。  如需這些範例中所使用間接取值運算子 \(**\***\) 的詳細資訊，請參閱[間接取值和傳址運算子](../c-language/indirection-and-address-of-operators.md)。  
  
```  
struct pair   
{  
    int a;  
    int b;  
    struct pair *sp;  
} item, list[10];  
```  
  
 `item` 結構的成員選取運算式如下所示：  
  
```  
item.sp = &item;  
```  
  
 在上面的範例中，`item` 結構的位址會指派給結構的 `sp` 成員。  這表示，`item` 包含本身的指標。  
  
```  
(item.sp)–>a = 24;  
```  
  
 在這個範例中，指標運算式 `item.sp` 會搭配成員選取運算子 \(**–\>**\) 用來將值指派給 `a` 成員。  
  
```  
list[8].b = 12;  
```  
  
 這個陳述式將說明如何從結構陣列選取個別結構成員。  
  
## 請參閱  
 [成員存取運算子：. 和 \-\>](../cpp/member-access-operators-dot-and.md)