---
title: 編譯器錯誤 C3230 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3230
dev_langs:
- C++
helpviewer_keywords:
- C3230
ms.assetid: 5ec53f25-59f6-4801-81e7-7b68bf04994d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f74e17b1dec3aba78a38d993da81995d00c93784
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46065593"
---
# <a name="compiler-error-c3230"></a>編譯器錯誤 C3230

'function' : 'template' 的樣板類型引數不可包含泛型類型參數: 'param'

樣板會在編譯時期具現化，但泛型會在執行階段具現化。 因此，您無法產生可呼叫樣板的泛型程式碼，因為當泛型類型最後確定時，無法於該執行階段具現化樣板。

下列範例會產生 C3230：

```
// C3230.cpp
// compile with: /clr /LD
template <class S>
void f(S t);

generic <class U>
ref class C {
   void f1(U x) {
      f(x);   // C3230
   }
};
```