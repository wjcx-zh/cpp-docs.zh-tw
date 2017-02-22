---
title: "函式樣板的明確特製化 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "宣告函式, 函式樣板的特製化"
  - "函式樣板的明確特製化"
  - "函式樣板, 特製化"
  - "覆寫, 函式"
  - "函式樣板的特製化"
ms.assetid: eb0fcb73-eaed-42a1-9b83-14b055a34bf8
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 函式樣板的明確特製化
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

透過函式樣板，您可以提供該類型的明確特製化 \(覆寫\) 函式樣板，來定義該特定類型的特殊行為。  例如：  
  
```  
template<> void MySwap(double a, double b);  
```  
  
 這個宣告可讓您為 **double** 變數定義不同的函式。  如同非樣板函式，會套用標準類型轉換 \(例如將 **float** 類型的變數提升為 **double**\)。  
  
## 範例  
  
```  
// explicit_specialization.cpp  
template<class T> void f(T t)  
{  
};  
  
// Explicit specialization of f with 'char' with the  
// template argument explicitly specified:  
//  
template<> void f<char>(char c)  
{  
}  
  
// Explicit specialization of f with 'double' with the  
// template argument deduced:  
//  
template<> void f(double d)  
{  
}  
int main()  
{  
}  
```  
  
## 請參閱  
 [函式樣板](../cpp/function-templates.md)