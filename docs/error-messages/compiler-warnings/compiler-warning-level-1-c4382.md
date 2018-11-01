---
title: 編譯器警告 (層級 1) C4382
ms.date: 11/04/2016
f1_keywords:
- C4382
helpviewer_keywords:
- C4382
ms.assetid: 34be9ad3-bae6-411a-8f80-0c8fd0d2c092
ms.openlocfilehash: cca2f8cc13cc8317bac3736e142ef58e126ed994
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50629212"
---
# <a name="compiler-warning-level-1-c4382"></a>編譯器警告 (層級 1) C4382

> 擲回 '*型別*': 具有 __clrcall 解構函式或複製建構函式的型別可能只會攔截在 /clr: pure 模組

## <a name="remarks"></a>備註

**/Clr: pure**編譯器選項是在 Visual Studio 2015 中已被取代，不支援的 Visual Studio 2017 中。

編譯時 **/clr** (不 **/clr: pure**)，例外狀況處理會預期要有成員函式是原生型別[__cdecl](../../cpp/cdecl.md)而非[__clrcall](../../cpp/clrcall.md). 搭配使用的成員函式的原生型別`__clrcall`無法攔截在編譯的模組中，呼叫慣例 **/clr**。

如果將編譯模組中攔截例外狀況 **/clr: pure**，您可以忽略此警告。

如需詳細資訊，請參閱 [/clr (Common Language Runtime 編譯)](../../build/reference/clr-common-language-runtime-compilation.md)。

## <a name="example"></a>範例

下列範例會產生 C4382。

```cpp
// C4382.cpp
// compile with: /clr /W1 /c
struct S {
   __clrcall ~S() {}
};

struct T {
   ~T() {}
};

int main() {
   S s;
   throw s;   // C4382

   S * ps = &s;
   throw ps;   // OK

   T t;
   throw t;   // OK
}
```