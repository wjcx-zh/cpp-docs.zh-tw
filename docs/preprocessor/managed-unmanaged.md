---
title: managed、unmanaged pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.unmanaged
- managed_CPP
- unmanaged_CPP
- vc-pragma.managed
helpviewer_keywords:
- managed pragma
- pragmas, unmanaged
- pragmas, managed
- unmanaged pragma
ms.assetid: f072ddcc-e1ec-408a-8ce1-326ddb60e4a4
ms.openlocfilehash: 4c13155d1c84966a593df11baf525a0c3539f02c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218804"
---
# <a name="managed-unmanaged-pragmas"></a>managed、unmanaged pragma

啟用函式層級控制項, 將函式編譯為 managed 或非受控。

## <a name="syntax"></a>語法

> **#pragma 管理**\
> **#pragma 非受控**\
> **#pragma 受控 (** [ **push,** ] { **on**  |  **off** } **)** \
> **#pragma 管理 (pop)**

## <a name="remarks"></a>備註

[/Clr](../build/reference/clr-common-language-runtime-compilation.md)編譯器選項提供模組層級的控制項, 可將函式編譯為 managed 或非受控。

針對原生平臺, 將會編譯非受控函式。 執行程式的該部分會由 common language runtime 傳遞至原生平臺。

預設會在使用 `/clr` 時編譯 Unmanaged 函式。

套用這些 pragma 時：

- 在函式前面加上 pragma, 而不是在函式主體內。

- 將 pragma 新增到 `#include` 陳述式之後。 請不要在語句之前`#include`使用這些 pragma。

如果未`/clr`在編譯中使用, 編譯器會忽略 managed 和非**受控**pragma。

當樣板函式具現化時, 定義範本時的 pragma 狀態會決定其是否為受控或未受管理。

如需詳細資訊, 請參閱[混合元件的初始化](../dotnet/initialization-of-mixed-assemblies.md)。

## <a name="example"></a>範例

```cpp
// pragma_directives_managed_unmanaged.cpp
// compile with: /clr
#include <stdio.h>

// func1 is managed
void func1() {
   System::Console::WriteLine("In managed function.");
}

// #pragma unmanaged
// push managed state on to stack and set unmanaged state
#pragma managed(push, off)

// func2 is unmanaged
void func2() {
   printf("In unmanaged function.\n");
}

// #pragma managed
#pragma managed(pop)

// main is managed
int main() {
   func1();
   func2();
}
```

```Output
In managed function.
In unmanaged function.
```

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
