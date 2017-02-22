---
title: "編譯器錯誤 C3714 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3714"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3714"
ms.assetid: 17718f75-5a37-4e42-912b-487e91008a95
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 編譯器錯誤 C3714
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'method' : 事件常式處理方法必須與來源 'method' 有相同的呼叫慣例  
  
 您定義了與來源事件方法使用不同呼叫慣例的事件處理常式方法。  若要修復此錯誤，請提供事件處理常式方法與來源事件方法相同的呼叫慣例。  例如，在下列程式碼中，讓 `handler1` 與 `event1` 的呼叫慣例相符 \([\_\_cdecl](../../cpp/cdecl.md) 或 [\_\_stdcall](../../cpp/stdcall.md) 或其他\)。  同時從兩個宣告移除呼叫慣例關鍵字也可以解決此問題，而且讓 `event1` 和 `handler1` 預設值為 [thiscall](../../cpp/thiscall.md) 呼叫慣例。  如需詳細資訊，請參閱[Calling Conventions](../../cpp/calling-conventions.md)。  
  
 下列範例會產生 C3714：  
  
```  
// C3714.cpp  
// compile with: /c  
// processor: x86  
[event_source(native)]  
class CEventSrc {  
public:  
   __event void __cdecl event1();  
   // try the following line instead  
   // __event void __stdcall event1();  
};  
  
[event_receiver(native)]  
class CEventRec {  
public:  
   void __stdcall handler1() {}  
  
   void HookEvents(CEventSrc* pSrc) {  
      __hook(&CEventSrc::event1, pSrc, &CEventRec::handler1);   // C3714  
   }  
  
   void UnhookEvents(CEventSrc* pSrc) {  
      __unhook(&CEventSrc::event1, pSrc, &CEventRec::handler1); // C3714  
   }  
};  
```