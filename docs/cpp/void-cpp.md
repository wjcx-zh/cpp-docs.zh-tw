---
title: "void (C++) | Microsoft Docs"
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
  - "void"
  - "void_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "函式 [C++], void"
  - "指標, void"
  - "void 關鍵字 [C++]"
ms.assetid: d203edba-38e6-4056-8b89-011437351057
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# void (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

做為函式傳回類型時，`void` 關鍵字指定該函式不會傳回值。  用於函式參數清單時，void 指定函式不接受參數。  當用於指標的宣告，void 指定指標是「通用的」。  
  
 如果指標的類型是 **void \***，指標可以指向不是以 **const** 或 `volatile` 關鍵字宣告的任何變數。  除非它轉換為其他類型，否則 void 指標無法取值。  Void 指標可以轉換成任何其他類型的資料指標。  
  
 Void 指標可以指向函式，但是不能指向 C\+\+ 的類別成員。  
  
 您不能宣告 void 類型的變數。  
  
## 範例  
  
```  
// void.cpp  
void vobject;   // C2182  
void *pv;   // okay  
int *pint; int i;  
int main() {  
   pv = &i;  
   // Cast optional in C required in C++  
   pint = (int *)pv;  
}   
```  
  
## 請參閱  
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)   
 [類型 void 的指標](../misc/pointers-to-type-void.md)   
 [基本類型](../cpp/fundamental-types-cpp.md)