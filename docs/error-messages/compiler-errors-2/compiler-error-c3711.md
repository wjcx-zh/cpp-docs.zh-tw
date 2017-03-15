---
title: "編譯器錯誤 C3711 | Microsoft Docs"
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
  - "C3711"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3711"
ms.assetid: 26d581cc-2153-4ee0-b814-a371184be3e1
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3711
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'method' : Unmanaged 事件來源方法必須傳回 void 或整數類資料型別  
  
 您在沒有傳回虛值或整數類資料型別 \(Integral Type\) 的事件來源中定義方法。  若要修復此錯誤，請讓事件和事件處理常式具有 `void` 的傳回型別，或是 `int` 和 `long` 之類的整數類資料型別。  
  
 下列範例會產生 C3711：  
  
```  
// C3711.cpp  
#include <atlbase.h>  
#include <atlcom.h>  
#include <atlctl.h>  
  
[event_source(native)]  
class CEventSrc {  
public:  
   __event float event1();   // C3711  
   // try the following line instead  
   // __event int event1();  
   // also change the handler, below  
};  
  
[event_receiver(native)]  
class CEventRec {  
public:  
   float handler1() {         // change float to int  
      return 0.0;             // change 0.0 to 0  
   }  
   void HookEvents(CEventSrc* pSrc) {  
      __hook(CEventSrc::event1, pSrc, CEventRec::handler1);  
   }  
   void UnhookEvents(CEventSrc* pSrc) {  
      __unhook(CEventSrc::event1, pSrc, CEventRec::handler1);  
   }  
};  
  
int main() {  
}  
```