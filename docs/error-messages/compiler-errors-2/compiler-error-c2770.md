---
title: "編譯器錯誤 C2770 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2770"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2770"
ms.assetid: 100001b5-80b0-4971-8ff6-9023f443c926
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器錯誤 C2770
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'template' 的無效明確 template\_or\_generic 引數  
  
 具有明確樣板或泛型引數的函式候選樣板，產生不允許的函式型別。  
  
 下列範例會產生 C2770：  
  
```  
// C2770.cpp  
#include <stdio.h>  
template <class T>  
int f(typename T::B*);   // expects type with member B  
  
struct Err {};  
  
int main() {  
   f<int>(0);   // C2770 int has no B  
   // try the following line instead  
   f<OK>(0);  
}  
```