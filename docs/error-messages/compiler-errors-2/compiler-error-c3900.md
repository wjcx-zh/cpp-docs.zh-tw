---
title: "編譯器錯誤 C3900 | Microsoft Docs"
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
  - "C3900"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3900"
ms.assetid: a94cc561-8fa8-4344-9e01-e81ff462fae5
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3900
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'member': 目前的範圍中不允許  
  
 屬性區塊只能包含函式宣告和內嵌函式。  除了函式以外，屬性區塊中不允許任何成員。  也不允許任何 typedef、運算子或 friend 函式。  如需詳細資訊，請參閱[屬性](../../windows/property-cpp-component-extensions.md)。  
  
 事件定義只能包含存取方法和函式。  
  
 下列範例會產生 C3900：  
  
```  
// C3900.cpp  
// compile with: /clr  
ref class X {  
   property int P {  
      void set(int);   // OK  
      int i;   // C3900 variable declaration  
   };  
};  
```  
  
 下列範例會產生 C3900：  
  
```  
// C3900b.cpp  
// compile with: /clr  
using namespace System;  
delegate void H();  
ref class X {  
   event H^ E {  
      int m;   // C3900  
  
      // OK  
      void Test() {}  
  
      void add( H^ h ) {}  
      void remove( H^ h ) {}  
      void raise( ) {}  
   }  
};  
```