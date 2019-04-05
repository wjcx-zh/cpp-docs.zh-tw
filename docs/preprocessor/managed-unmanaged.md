---
title: managed、unmanaged
ms.date: 11/04/2016
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
ms.openlocfilehash: 7fa1e3274b85faa9f3f72f4db5bf586ee5d8e274
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59022342"
---
# <a name="managed-unmanaged"></a>managed、unmanaged
啟用函式層級控制項，用於編譯 Managed 或 Unmanaged 的函式。

## <a name="syntax"></a>語法

```
#pragma managed
#pragma unmanaged
#pragma managed([push,] on | off)
#pragma managed(pop)
```

## <a name="remarks"></a>備註

[/Clr](../build/reference/clr-common-language-runtime-compilation.md)編譯器選項提供模組層級的控制來編譯 managed 或 unmanaged 的函式。

編譯 Unmanaged 函式用於原生平台，Common Language Runtime 會將該部分的程式執行傳遞至該原生平台。

預設會在使用 `/clr` 時編譯 Unmanaged 函式。

套用這些 pragma 時：

- 將 pragma 新增到函式之前而不是函式主體之內。

- 將 pragma 新增到 `#include` 陳述式之後。 請勿在 `#include` 陳述式之前使用這些 pragma。

編譯器會忽略**受控**並**unmanaged** pragma 如果`/clr`不會在編譯中。

具現化樣板函式時，定義樣板時的 pragma 狀態決定函式為 Managed 或 Unmanaged 函式。

如需詳細資訊，請參閱 <<c0> [ 初始化混合組件](../dotnet/initialization-of-mixed-assemblies.md)。

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

[Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)