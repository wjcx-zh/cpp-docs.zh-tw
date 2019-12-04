---
title: 編譯器錯誤 C2743
ms.date: 11/04/2016
f1_keywords:
- C2743
helpviewer_keywords:
- C2743
ms.assetid: 644cd444-21d2-471d-a176-f5f52c5a0b73
ms.openlocfilehash: d679ce0df0d43772a6c32aa8e00869ac1a4a082b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759642"
---
# <a name="compiler-error-c2743"></a>編譯器錯誤 C2743

' type '：無法使用 __clrcall 的析構函式或複製模式來攔截原生類型

以 **/clr**編譯的模組嘗試攔截原生類型的例外狀況，而此類型的析構函數或複製偵測器使用 `__clrcall` 呼叫慣例。

以 **/clr**編譯時，例外狀況處理會預期原生類型中的成員函式會[__cdecl](../../cpp/cdecl.md) ，而不是[__clrcall](../../cpp/clrcall.md)。 具有使用 `__clrcall` 呼叫慣例之成員函式的原生類型，無法在使用 **/clr**編譯的模組中攔截。

如需詳細資訊，請參閱 [/clr (Common Language Runtime 編譯)](../../build/reference/clr-common-language-runtime-compilation.md)。

## <a name="example"></a>範例

下列範例會產生 C2743。

```cpp
// C2743.cpp
// compile with: /clr
public struct S {
   __clrcall ~S() {}
};

public struct T {
   ~T() {}
};

int main() {
   try {}
   catch(S) {}   // C2743
   // try the following line instead
   // catch(T) {}

   try {}
   catch(S*) {}   // OK
}
```
