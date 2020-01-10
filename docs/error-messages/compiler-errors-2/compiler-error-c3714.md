---
title: 編譯器錯誤 C3714
ms.date: 11/04/2016
f1_keywords:
- C3714
helpviewer_keywords:
- C3714
ms.assetid: 17718f75-5a37-4e42-912b-487e91008a95
ms.openlocfilehash: 1078bf8a97f6cb7afeaf7046489fe262c0bb0199
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74753324"
---
# <a name="compiler-error-c3714"></a>編譯器錯誤 C3714

' method '：事件處理常式方法必須與來源 ' method ' 具有相同的呼叫慣例

您定義的事件處理常式方法，並未使用與來源事件方法相同的呼叫慣例。 若要修正此錯誤，請為事件處理常式方法提供與來源事件方法相同的呼叫慣例。 例如，在下列程式碼中，請 `handler1` 的呼叫慣例和 `event1` 相符（[__cdecl](../../cpp/cdecl.md)或[__stdcall](../../cpp/stdcall.md)或其他專案）。 從這兩個宣告中移除呼叫慣例關鍵字也會解決此問題，並導致 `event1` 和 `handler1` 預設為[thiscall](../../cpp/thiscall.md)呼叫慣例。 如需詳細資訊，請參閱[呼叫慣例](../../cpp/calling-conventions.md)。

下列範例會產生 C3714：

```cpp
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
