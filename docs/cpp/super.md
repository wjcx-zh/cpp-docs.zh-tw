---
title: "__super | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__super_cpp"
  - "__super"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__super 關鍵字 [C++]"
ms.assetid: f0957c31-9256-405b-b402-cad182404b5f
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# __super
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 可讓您明確陳述您要呼叫將覆寫之函式的基底類別實作。  
  
## 語法  
  
```  
  
__super::  
member_function  
();  
  
```  
  
## 備註  
 多載解析階段會考量所有可存取的基底類別方法，並且提供最佳相符結果的函式即為將會呼叫的函式。  
  
 `__super` 只能出現在成員函式的主體中。  
  
 `__super` 不能與 using 宣告搭配使用。  如需詳細資訊，請參閱 [using 宣告](../cpp/using-declaration.md)。  
  
 引入插入程式碼的[屬性](../windows/cpp-attributes-reference.md)時，您的程式碼可能會包含一個或多個基底類別，而您可能不知道這些類別的名稱，但其中包含您想要呼叫的方法。  
  
## 範例  
  
```  
// deriv_super.cpp  
// compile with: /c  
struct B1 {  
   void mf(int) {}  
};  
  
struct B2 {  
   void mf(short) {}  
  
   void mf(char) {}  
};  
  
struct D : B1, B2 {  
   void mf(short) {  
      __super::mf(1);   // Calls B1::mf(int)  
      __super::mf('s');   // Calls B2::mf(char)  
   }  
};  
```  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)