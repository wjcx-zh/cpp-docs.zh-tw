---
title: "編譯器錯誤 C3738 | Microsoft Docs"
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
  - "C3738"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3738"
ms.assetid: dd3ee011-e204-4264-bf3a-da32c4ef7038
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3738
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'calling\_convention': 明確具現化的呼叫慣例，必須符合所要具現化的樣板的呼叫慣例  
  
 建議您，不要在明確具現化上指定呼叫慣例。  但如果非指定不可，呼叫慣例必須相符。  
  
## 範例  
 下列範例會產生 C3738。  
  
```  
// C3738.cpp  
// compile with: /clr  
// processor: x86  
#include <stdio.h>  
template< class T >  
void f ( T arg ) {   // by default calling convention is __cdecl  
   printf ( "f: %s\n", __FUNCSIG__ );  
}  
  
template   
void __stdcall f< int > ( int arg );   // C3738  
// try the following line instead  
// void f< int > ( int arg );  
  
int main () {  
   f(1);  
   f< int > ( 1 );  
}  
```