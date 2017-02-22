---
title: "編譯器警告 (層級 1) C4584 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4584"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4584"
ms.assetid: ad86582f-cb8c-4d21-8c4c-a6c800059e25
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 編譯器警告 (層級 1) C4584
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'class1' : 基底類別 'class2' 已經是 'class3' 的基底類別  
  
 您定義的類別繼承自兩個類別，而其中一個類別繼承自另一個。  例如：  
  
```  
// C4584.cpp  
// compile with: /W1 /LD  
class A {  
};  
  
class B : public A {  
};  
  
class C : public A, public B { // C4584  
};  
```  
  
 在這種情況下，類別 C 會發出警告，因為它同時繼承自類別 A 和也是繼承自類別 A 的類別 B。  此警告的作用是在提醒您必須完全限定使用來自這些基底類別的成員，否則會因為無法得知您所參考的成員，繼而產生模稜兩可的情況而造成編譯器錯誤。