---
title: "編譯器錯誤 C3745 | Microsoft Docs"
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
  - "C3745"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3745"
ms.assetid: 1e64aec5-7e53-47e5-bc7d-3905230cfc66
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3745
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : 只有事件可以 'raised'  
  
 只有用 [\_\_event](../../cpp/event.md) 關鍵字定義的函式可以被傳遞至 [\_\_raise](../../cpp/raise.md) 關鍵字。  
  
 下列範例會產生 C3745：  
  
```  
// C3745.cpp  
struct E {  
   __event void func();  
   void func(int) {  
   }  
  
   void func2() {  
   }  
  
   void bar() {  
      __raise func();  
      __raise func(1);   // C3745  
      __raise func2();   // C3745  
   }  
};  
  
int main() {  
   E e;  
   __raise e.func();  
   __raise e.func(1);   // C3745  
   __raise e.func2();   // C3745  
}  
```