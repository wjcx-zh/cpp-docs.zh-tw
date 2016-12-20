---
title: "編譯器錯誤 C2275 | Microsoft Docs"
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
  - "C2275"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2275"
ms.assetid: c1eafa71-48de-46e0-82f3-b575538ef205
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2275
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 將此型別當做運算式的使用方式不合法  
  
 運算式以 `->` 運算子配合 `typedef` 識別項使用。  
  
 下列範例會產生 C2275：  
  
```  
// C2275.cpp  
typedef struct S {  
    int mem;  
} *S_t;  
void func1( int *parm );  
void func2() {  
    func1( &S_t->mem );   // C2275, S_t is a typedef  
}  
```