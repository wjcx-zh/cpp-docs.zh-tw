---
title: 編譯器錯誤 C3068 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3068
dev_langs:
- C++
helpviewer_keywords:
- C3068
ms.assetid: 613e3447-b4a8-4268-a661-297bed63ccdf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fdea26e204032c27f00639ee46a928c7bf084a4e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035615"
---
# <a name="compiler-error-c3068"></a>編譯器錯誤 C3068

'function': 'naked' 函式不能包含需要的物件會回溯發生 c + + 例外狀況

編譯器無法執行上的堆疊回溯[naked](../../cpp/naked-cpp.md)擲回例外狀況，因為暫存物件建立在函式和 c + + 例外狀況處理函式 ([/EHsc](../../build/reference/eh-exception-handling-model.md)) 指定。

若要解決這個錯誤，執行至少下列其中一：

- 未使用 /EHsc 編譯。

- 請勿將標示為函式`naked`。

- 請勿在函式建立暫存物件。

如果函式在堆疊上，建立暫存物件，如果函式會擲回的例外狀況，而且如果啟用 c + + 例外狀況處理，編譯器將會清除堆疊在擲回例外狀況。

當發生例外狀況時，編譯器產生的程式碼，呼叫的初構和終解但不會出現在 naked 函式時，會執行函式。

## <a name="example"></a>範例

下列範例會產生 C3068:

```
// C3068.cpp
// compile with: /EHsc
// processor: x86
class A {
public:
   A(){}
   ~A(){}
};

void b(A){}

__declspec(naked) void c() {
   b(A());   // C3068
};
```