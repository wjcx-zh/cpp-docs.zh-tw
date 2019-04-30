---
title: 編譯器錯誤 C3068
ms.date: 11/04/2016
f1_keywords:
- C3068
helpviewer_keywords:
- C3068
ms.assetid: 613e3447-b4a8-4268-a661-297bed63ccdf
ms.openlocfilehash: 4790c9caafd28722f3631104cfe5cfc762cf6426
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406882"
---
# <a name="compiler-error-c3068"></a>編譯器錯誤 C3068

'function': 'naked' 函式不能包含會需要物件回溯如果C++發生例外狀況

編譯器無法執行上的堆疊回溯[naked](../../cpp/naked-cpp.md)擲回例外狀況，因為暫存物件建立函式中的函式和C++例外狀況處理 ([/EHsc](../../build/reference/eh-exception-handling-model.md)) 是指定此項目。

若要解決這個錯誤，執行至少下列其中一：

- 未使用 /EHsc 編譯。

- 請勿將標示為函式`naked`。

- 請勿在函式建立暫存物件。

如果函式會建立暫存物件在堆疊上，如果函式會擲回的例外狀況，而且C++例外狀況處理功能啟用後，編譯器將會清除堆疊在擲回例外狀況。

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