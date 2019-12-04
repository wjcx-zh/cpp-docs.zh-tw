---
title: 編譯器錯誤 C2346
ms.date: 11/04/2016
f1_keywords:
- C2346
helpviewer_keywords:
- C2346
ms.assetid: 246145be-5645-4cd6-867c-e3bc39e33dca
ms.openlocfilehash: fc2aeac02ecc3f29406c2288051ca6cd9d3a4923
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760006"
---
# <a name="compiler-error-c2346"></a>編譯器錯誤 C2346

' function ' 無法編譯為原生：原因

編譯器無法將函式編譯為 MSIL。

如需詳細資訊，請參閱[managed、非受控](../../preprocessor/managed-unmanaged.md)和[/Clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)。

### <a name="to-correct-this-error"></a>若要改正這項錯誤

1. 移除無法編譯為 MSIL 的函式中的程式碼。

1. 請不要使用 **/clr**編譯模組，或將函式標記為非受控 pragma。

## <a name="example"></a>範例

下列範例會產生 C2346。

```cpp
// C2346.cpp
// processor: x86
// compile with: /clr
// C2346 expected
struct S
{
   S()
   {
      { __asm { nop } }
   }
   virtual __clrcall ~S() { }
};

void main()
{
   S s;
}
```
