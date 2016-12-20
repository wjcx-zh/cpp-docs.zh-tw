---
title: "編譯器警告 (層級 1) C4812 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4812"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4812"
ms.assetid: a7f5721f-2019-44de-ad62-ed30bac8b1f3
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4812
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

過時的宣告樣式：請用 'new\_syntax' 代替  
  
 在目前的 Visual C\+\+ 版本中，仍然支援明確建構函式特製化，但未來的版本可能不予支援。  
  
 下列範例會產生 C4812：  
  
```  
// C4812.cpp // compile with: /W1 /c template <class T> class MyClass; template<class T> class MyClass<T*> { MyClass(); }; template<class T> MyClass<T*>::MyClass<T*>() {}   // C4812 // try the following line instead // MyClass<T*>::MyClass() {}  
```