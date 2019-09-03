---
title: fenv_access pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.fenv_access
- fenv_access_CPP
helpviewer_keywords:
- pragmas, fenv_access
- fenv_access pragma
ms.assetid: 2ccea292-0ae4-42ce-9c67-cc189299857b
ms.openlocfilehash: c8e66881bde12df28bf24e18230471cb4caca792
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218601"
---
# <a name="fenv_access-pragma"></a>fenv_access pragma

停用 (**開啟**) 或啟用 (**關閉**) 可能會變更浮點環境旗標測試和模式變更的優化。

## <a name="syntax"></a>語法

> **#pragma fenv_access (** { **on** | **off** } **)**

## <a name="remarks"></a>備註

根據預設, **fenv_access**為**off**。 如果編譯器會假設您的程式碼不會存取或操作浮點環境, 則它可以執行許多浮點程式碼優化。 將 [ **fenv_access** ] 設定為 [**開啟**], 以通知編譯器您的程式碼會存取浮點環境, 以測試狀態旗標、例外狀況, 或設定控制模式旗標。 編譯器會停用這些優化, 讓您的程式碼可以一致地存取浮點環境。

如需浮點行為的詳細資訊, 請參閱[/fp (指定浮點行為)](../build/reference/fp-specify-floating-point-behavior.md)。

受限於**fenv_access**的優化類型如下:

- 全域通用子運算式刪除

- 程式碼移動

- 常數摺疊

其他浮點 pragma 包括：

- [float_control](../preprocessor/float-control.md)

- [fp_contract](../preprocessor/fp-contract.md)

## <a name="examples"></a>範例

這個範例會將**fenv_access**設定為**on** , 以將浮點控制暫存器設定為24位有效位數:

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

如果您`#pragma fenv_access (on)`從上一個範例中加上批註, 請注意輸出會有所不同, 因為編譯器會進行編譯時間評估, 而不會使用控制模式。

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

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
