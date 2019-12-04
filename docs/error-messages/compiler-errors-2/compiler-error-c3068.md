---
title: 編譯器錯誤 C3068
ms.date: 11/04/2016
f1_keywords:
- C3068
helpviewer_keywords:
- C3068
ms.assetid: 613e3447-b4a8-4268-a661-297bed63ccdf
ms.openlocfilehash: 9e20333a4fc18219f7f2514f3aefe73b81f284a6
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759486"
---
# <a name="compiler-error-c3068"></a>編譯器錯誤 C3068

' function '： ' naked ' 函式不能包含在發生C++例外狀況時必須回溯的物件

編譯器無法在擲回例外狀況的[naked](../../cpp/naked-cpp.md)函數上執行堆疊回溯，因為已在函式中建立暫存物件，而且C++已指定例外狀況處理（[/ehsc](../../build/reference/eh-exception-handling-model.md)）。

若要解決此錯誤，請至少執行下列其中一項動作：

- 不使用/EHsc. 進行編譯

- 請勿將函數標示為 `naked`。

- 請勿在函數中建立暫存物件。

如果函式在堆疊上建立暫存物件，且函式擲回例外狀況，而且如果C++已啟用例外狀況處理，則編譯器會在擲回例外狀況時清除堆疊。

當擲回例外狀況時，會針對函式執行編譯器產生的程式碼（稱為初構和終解，而不存在於 naked 函數中）。

## <a name="example"></a>範例

下列範例會產生 C3068：

```cpp
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
