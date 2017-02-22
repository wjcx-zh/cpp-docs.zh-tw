---
title: "編譯器錯誤 C3200 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3200"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3200"
ms.assetid: 44bb5e77-f0ec-421c-a732-b9ee7c0a3529
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# 編譯器錯誤 C3200
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'template' : 樣板參數 'parameter' 的無效樣板引數，必須是類別樣板  
  
 您將一個無效的引數傳遞至類別樣板。  類別樣板必須要以樣板做為參數。  在以下範例中，呼叫 `Y<int, int> aY` 將會產生 C3200。  第一個參數必須是樣板，例如 `Y<X, int> aY`。  
  
```  
// C3200.cpp  
template<typename T>  
class X  
{  
};  
  
template<template<typename U> class T1, typename T2>  
class Y  
{  
};  
  
int main()  
{  
   Y<int, int> y;   // C3200  
}  
```