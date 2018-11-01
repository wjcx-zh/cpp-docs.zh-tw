---
title: 編譯器錯誤 C2743
ms.date: 11/04/2016
f1_keywords:
- C2743
helpviewer_keywords:
- C2743
ms.assetid: 644cd444-21d2-471d-a176-f5f52c5a0b73
ms.openlocfilehash: 03cd7c13e093be5073b3df7e7cf29dda870bc47a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50530993"
---
# <a name="compiler-error-c2743"></a>編譯器錯誤 C2743

'type': 無法攔截具有 __clrcall 解構函式或複製建構函式的原生型別

模組編譯 **/clr**嘗試攔截例外狀況的原生類型和類型的解構函式或複製建構函式會使用其中`__clrcall`呼叫慣例。

編譯時 **/clr**，例外狀況處理會預期要有成員函式是原生型別[__cdecl](../../cpp/cdecl.md)而非[__clrcall](../../cpp/clrcall.md)。 搭配使用的成員函式的原生型別`__clrcall`無法攔截在編譯的模組中，呼叫慣例 **/clr**。

如需詳細資訊，請參閱 [/clr (Common Language Runtime 編譯)](../../build/reference/clr-common-language-runtime-compilation.md)。

## <a name="example"></a>範例

下列範例會產生 C2743。

```
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