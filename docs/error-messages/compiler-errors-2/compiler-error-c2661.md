---
title: "編譯器錯誤 C2661 | Microsoft Docs"
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
  - "C2661"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2661"
ms.assetid: 60021467-71cd-451b-9877-23840c69309f
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2661
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : 多載函式不使用 number 參數  
  
 可能的原因：  
  
1.  函式呼叫中不正確的實質參數。  
  
2.  遺漏函式宣告。  
  
 下列範例會產生 C2661：  
  
```  
// C2661.cpp  
void func( int ){}  
void func( int, int ){}  
int main() {  
   func( );   // C2661 func( void ) was not declared  
   func( 1 );   // OK func( int ) was declared  
}  
```