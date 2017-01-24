---
title: "編譯器錯誤 C3231 | Microsoft Docs"
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
  - "C3231"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3231"
ms.assetid: fe5dc352-e634-45fa-9534-3da176294c98
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3231
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'arg' : 樣板類型引數不可使用泛型型別參數  
  
 樣板是在編譯時期具現化，但泛型是在執行階段具現化。  因此不可能產生呼叫樣板的泛型程式碼，因為在最後知道泛型型別時，樣板不能在執行階段具現化。  
  
 下列範例會產生 C3231：  
  
```  
// C3231.cpp  
// compile with: /clr /LD  
template <class T> class A;  
  
generic <class T>  
ref class C {  
   void f() {  
      A<T> a;   // C3231  
   }  
};  
```