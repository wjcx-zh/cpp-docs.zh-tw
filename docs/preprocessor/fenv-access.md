---
title: fenv_access |Microsoft 文件
ms.custom: ''
ms.date: 03/12/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.fenv_access
- fenv_access_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, fenv_access
- fenv_access pragma
ms.assetid: 2ccea292-0ae4-42ce-9c67-cc189299857b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f74f20b1dcb20c1449d21e91181f8bfb17075b7e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33912962"
---
# <a name="fenvaccess"></a>fenv_access

停用 (**上**) 或啟用 (**關閉*) 可以變更浮點環境的最佳化旗標測試和模式變更。

## <a name="syntax"></a>語法

> **#pragma fenv_access (** {**上** | **關閉**} **)**  

## <a name="remarks"></a>備註

根據預設， **fenv_access**是**關閉**。 如果編譯器可能會假設您的程式碼不會存取或操作浮點數的環境中，則它可以執行許多的浮點程式碼最佳化。 設定**fenv_access**至**上**通知編譯器將程式碼會存取浮點數的環境來測試狀態旗標，例外狀況，或設定控制項模式的旗標。 編譯器會停用這些最佳化，使您的程式碼可以一直存取浮點數的環境。 

如需有關浮點數行為的詳細資訊，請參閱[/fp （指定浮點行為）](../build/reference/fp-specify-floating-point-behavior.md)。

都受限於的最佳化類型**fenv_access**是：

- 全域通用子運算式刪除

- 程式碼移動

- 常數摺疊

其他浮點 pragma 包括：

- [float_control](../preprocessor/float-control.md)

- [fp_contract](../preprocessor/fp-contract.md)

## <a name="examples"></a>範例

此範例會設定**fenv_access**至**上**設為 24 位元精確度的浮點控制暫存器：

```cpp
// pragma_directive_fenv_access_x86.cpp
// compile with: /O2
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
out=9.999999776482582e-003
```

如果您註解`#pragma fenv_access (on)`從先前的範例，請注意，輸出會不同，因為編譯器會產生編譯時期求值，而不使用控制模式。

```cpp
// pragma_directive_fenv_access_2.cpp
// compile with: /O2
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
out=1.000000000000000e-002
```

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
