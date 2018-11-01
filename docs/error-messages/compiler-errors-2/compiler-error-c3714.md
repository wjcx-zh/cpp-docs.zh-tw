---
title: 編譯器錯誤 C3714
ms.date: 11/04/2016
f1_keywords:
- C3714
helpviewer_keywords:
- C3714
ms.assetid: 17718f75-5a37-4e42-912b-487e91008a95
ms.openlocfilehash: 9bfdf8b26ab599ef1a28483af7ebc28f0dbc1912
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50441869"
---
# <a name="compiler-error-c3714"></a>編譯器錯誤 C3714

'method': 事件處理常式方法必須有相同的呼叫慣例做為來源 'method'

您定義未使用相同的呼叫慣例與來源事件方法的事件處理常式方法。 若要修正這個錯誤，讓事件處理常式方法的來源事件方法相同的呼叫慣例。 例如，下列程式碼，進行的呼叫慣例`handler1`並`event1`比對 ([__cdecl](../../cpp/cdecl.md)或[__stdcall](../../cpp/stdcall.md)或其他人)。 移除從兩個宣告呼叫慣例關鍵字也會解決此問題，並會造成`event1`並`handler1`表示預設為[thiscall](../../cpp/thiscall.md)呼叫慣例。 請參閱[呼叫慣例](../../cpp/calling-conventions.md)如需詳細資訊。

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