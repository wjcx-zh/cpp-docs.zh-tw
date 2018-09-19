---
title: 編譯器錯誤 C3712 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3712
dev_langs:
- C++
helpviewer_keywords:
- C3712
ms.assetid: 65b1fcaf-be89-4c55-9e40-25ec03457253
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aa1790c2f5634f01d52e0eec65f5bfcf933ab058
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46029919"
---
# <a name="compiler-error-c3712"></a>編譯器錯誤 C3712

'method': 事件處理常式方法必須傳回相同的型別，做為來源 'method'

您定義事件處理常式方法不會傳回來源事件方法相同的型別。 若要修正這個錯誤，請提供事件處理常式方法相同的來源事件方法的傳回類型。

下列範例會產生 C3712:

```
// C3712.cpp
// compile with: /c
[event_source(native)]
class CEventSrc {
public:
   __event void event1();
};

[event_receiver(native)]
class CEventRec {
public:
   int handler1() { return 0; }
   // try the following line instead
   // void handler1() {}

   void HookEvents(CEventSrc* pSrc) {
      __hook(&CEventSrc::event1, pSrc, &CEventRec::handler1);   // C3712
   }
   void UnhookEvents(CEventSrc* pSrc) {
      __unhook(&CEventSrc::event1, pSrc, &CEventRec::handler1);   // C3712
   }
};
```