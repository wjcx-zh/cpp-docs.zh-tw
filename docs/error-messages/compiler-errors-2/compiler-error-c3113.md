---
title: "編譯器錯誤 C3113 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3113"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3113"
ms.assetid: 3afdc668-b29e-474e-9ea3-aa027d42db7c
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3113
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'structure' 不可為樣板\/泛型  
  
 您嘗試在介面或列舉之外使用類別樣板或類別泛型。  
  
 下列範例會產生 C3113：  
  
```  
// C3113.cpp  
// compile with: /c  
template <class T>   
enum E {};   // C3113  
// try the following line instead  
// class MyClass{};  
```