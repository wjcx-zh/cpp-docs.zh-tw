---
title: 編譯器錯誤 C3231 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3231
dev_langs:
- C++
helpviewer_keywords:
- C3231
ms.assetid: fe5dc352-e634-45fa-9534-3da176294c98
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 57727fbd71314201ec76119d37ab9c73b01d471d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46097305"
---
# <a name="compiler-error-c3231"></a>編譯器錯誤 C3231

'arg': 樣板類型引數不能使用泛型類型參數

樣板會在編譯時期具現化，但泛型會在執行階段具現化。 因此，您無法產生可呼叫樣板的泛型程式碼，因為當泛型類型最後確定時，無法於該執行階段具現化樣板。

下列範例會產生 C3231:

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