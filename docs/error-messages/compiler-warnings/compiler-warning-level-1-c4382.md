---
title: 編譯器警告 (層級 1) C4382
ms.date: 11/04/2016
f1_keywords:
- C4382
helpviewer_keywords:
- C4382
ms.assetid: 34be9ad3-bae6-411a-8f80-0c8fd0d2c092
ms.openlocfilehash: 7b8dbf77defab2a711ad931057c740193908474b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186968"
---
# <a name="compiler-warning-level-1-c4382"></a>編譯器警告 (層級 1) C4382

> 擲回 '*type*'：只能在/clr： pure 模組中攔截具有 __clrcall 的析構函數或複製處理函式的類型

## <a name="remarks"></a>備註

**/Clr： pure**編譯器選項在 Visual Studio 2015 中已被取代，在 Visual Studio 2017 中不支援。

以 **/clr** （不是 **/clr： pure**）進行編譯時，例外狀況處理會預期原生類型中的成員函式會[__cdecl](../../cpp/cdecl.md) ，而不是[__clrcall](../../cpp/clrcall.md)。 具有使用 `__clrcall` 呼叫慣例之成員函式的原生類型，無法在使用 **/clr**編譯的模組中攔截。

如果在以 **/clr： pure**編譯的模組中攔截到例外狀況，您可以忽略此警告。

如需詳細資訊，請參閱 [/clr (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md)。

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
