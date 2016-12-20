---
title: "編譯器錯誤 C3731 | Microsoft Docs"
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
  - "C3731"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3731"
ms.assetid: 45f89fcd-464c-4bc8-8a42-edcb5416d26c
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3731
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不相容的事件 'function1' 和處理常式 'function2'; 事件來源和事件處理常式必須有相同的事件型別  
  
 事件來源和事件接收者必須有相同的型別 \(例如 `native` 型別對比 `com` 型別 \)。  若要修復此錯誤，請使事件來源與事件處理常式的型別相符。  
  
 下列範例會產生 C3731：  
  
```  
// C3731.cpp  
// compile with: /clr  
#using <mscorlib.dll>  
[event_source(native)]  
struct A {  
   __event void MyEvent();  
};  
  
[event_receiver(managed)]  
// try the following line instead  
// [event_receiver(native)]  
struct B {  
   void func();  
   B(A a) {  
      __hook(&A::MyEvent, &a, &B::func);   // C3731  
   }  
};  
  
int main() {  
}  
```