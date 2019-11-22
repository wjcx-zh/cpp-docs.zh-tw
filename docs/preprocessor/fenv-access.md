---
title: fenv_access pragma
description: 描述 fenv_access pragma 指示詞的用法和效果。 Fenv_access 指示詞會控制在執行時間對浮點環境的存取。
ms.date: 11/19/2019
f1_keywords:
- vc-pragma.fenv_access
- fenv_access_CPP
helpviewer_keywords:
- pragmas, fenv_access
- fenv_access pragma
ms.assetid: 2ccea292-0ae4-42ce-9c67-cc189299857b
ms.openlocfilehash: e03eb404f2805a4f7c96509600c063c1b1acf629
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74305851"
---
# <a name="fenv_access-pragma"></a>fenv_access pragma

停用（**開啟**）或啟用（**關閉**）可能會變更浮點環境旗標測試和模式變更的優化。

## <a name="syntax"></a>語法

> **#pragma fenv_access （** { **on** | **off** } **）**

## <a name="remarks"></a>備註

**Fenv_access**預設為**關閉**。 編譯器會假設您的程式碼不會存取或操作浮點環境。 如果不需要環境存取，編譯器可以執行更多的動作來優化您的浮點程式碼。

如果您的程式碼會測試浮點狀態旗標、例外狀況或設定控制模式旗標，請啟用**fenv_access** 。 編譯器會停用浮點優化，因此您的程式碼可以一致地存取浮點環境。

[/Fp： strict] 命令列選項會自動啟用**fenv_access**。 如需有關這個和其他浮點行為的詳細資訊，請參閱[/fp （指定浮點行為）](../build/reference/fp-specify-floating-point-behavior.md)。

您可以使用**fenv_access** pragma 搭配其他浮點設定的方式有一些限制：

- 除非已啟用精確的語義，否則您無法啟用**fenv_access** 。 您可以透過[float_control](float-control.md) pragma 或使用[/fp：精確](../build/reference/fp-specify-floating-point-behavior.md)或[/fp： strict](../build/reference/fp-specify-floating-point-behavior.md)編譯器選項來啟用精確的語義。 如果未指定其他浮點命令列選項，編譯器會預設為 **/fp：精確**。

- 設定**fenv_access （on）** 時，您無法使用**float_control**來停用精確的語義。

受限於**fenv_access**的優化類型如下：

- 全域通用子運算式刪除

- 程式碼移動

- 常數摺疊

其他浮點 pragma 包括：

- [float_control](../preprocessor/float-control.md)

- [fp_contract](../preprocessor/fp-contract.md)

## <a name="examples"></a>範例

這個範例會將**fenv_access**設定為**on** ，以設定24位有效位數的浮點控制項暫存器：

```cpp
// pragma_directive_fenv_access_x86.cpp
// compile with: /O2 /arch:IA32
// processor: x86
#include <stdio.h>
#include <float.h>
#include <errno.h>
#pragma fenv_access (on)

int main() {
   double z, b = 0.1, t = 0.1;
   unsigned int currentControl;
   errno_t err;

   err = _controlfp_s(&currentControl, _PC_24, _MCW_PC);
   if (err != 0) {
      printf_s("The function _controlfp_s failed!\n");
      return -1;
   }
   z = b * t;
   printf_s ("out=%.15e\n",z);
}
```

```Output
out=9.999999776482582e-03
```

如果您將上一個範例中的 `#pragma fenv_access (on)` 批註，輸出就會不同。 這是因為編譯器會進行編譯時間評估，而不會使用控制模式。

```cpp
// pragma_directive_fenv_access_2.cpp
// compile with: /O2 /arch:IA32
#include <stdio.h>
#include <float.h>

int main() {
   double z, b = 0.1, t = 0.1;
   unsigned int currentControl;
   errno_t err;

   err = _controlfp_s(&currentControl, _PC_24, _MCW_PC);
   if (err != 0) {
      printf_s("The function _controlfp_s failed!\n");
      return -1;
   }
   z = b * t;
   printf_s ("out=%.15e\n",z);
}
```

```Output
out=1.000000000000000e-02
```

## <a name="see-also"></a>請參閱

[Pragma 指示詞和 __pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
