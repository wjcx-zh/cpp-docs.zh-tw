---
title: "編譯器錯誤 C3714 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3714
dev_langs:
- C++
helpviewer_keywords:
- C3714
ms.assetid: 17718f75-5a37-4e42-912b-487e91008a95
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 69f3f5c90524b02cad8a36babaceeb32544e7aff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3714"></a>編譯器錯誤 C3714
'method': 事件處理常式方法必須有相同的呼叫慣例做為來源 'method'  
  
 您已定義未使用相同的呼叫慣例做為來源事件方法的事件處理常式方法。 若要修正這個錯誤，讓事件處理常式方法相同的來源事件方法的呼叫慣例。 例如，下列程式碼，進行的呼叫慣例`handler1`和`event1`比對 ([__cdecl](../../cpp/cdecl.md)或[__stdcall](../../cpp/stdcall.md)或其他人)。 移除從兩個宣告呼叫慣例關鍵字也會解決問題，並會導致`event1`和`handler1`預設為[thiscall](../../cpp/thiscall.md)呼叫慣例。 請參閱[呼叫慣例](../../cpp/calling-conventions.md)如需詳細資訊。  
  
 下列範例會產生 C3714:  
  
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