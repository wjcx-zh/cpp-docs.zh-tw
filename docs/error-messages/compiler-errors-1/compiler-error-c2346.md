---
title: 編譯器錯誤 C2346
ms.date: 11/04/2016
f1_keywords:
- C2346
helpviewer_keywords:
- C2346
ms.assetid: 246145be-5645-4cd6-867c-e3bc39e33dca
ms.openlocfilehash: a6d75ca671e22203cb40ca18de21606834eeefa8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188087"
---
# <a name="compiler-error-c2346"></a>編譯器錯誤 C2346

'function' 無法編譯為原生： 原因

編譯器無法編譯為 MSIL 函式。

如需詳細資訊，請參閱 < [managed、 unmanaged](../../preprocessor/managed-unmanaged.md)並[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)。

### <a name="to-correct-this-error"></a>更正這個錯誤

1. 無法編譯為 MSIL 的函式中移除的程式碼。

1. 其中一個不會編譯的模組 **/clr**，或將標記為使用非受控 pragma unmanaged 函式。

## <a name="example"></a>範例

下列範例會產生 C2346。

```
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