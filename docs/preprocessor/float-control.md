---
title: float_control pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.float_control
- float_control_CPP
helpviewer_keywords:
- float_control pragma
- pragmas, float_control
ms.assetid: 4f4ba5cf-3707-413e-927d-5ecdbc0a9a43
ms.openlocfilehash: aa8cdc07953405175c1753791ab53214d73ba516
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218574"
---
# <a name="float_control-pragma"></a>float_control pragma

指定函式的浮點行為。

## <a name="syntax"></a>語法

> **#pragma float_control**\
> **#pragma float_control (** {**精確** | **嚴格** |  **,** **但**}, { **on**  |  **off** } [ **, push** ] **)** \
> **#pragma float_control (** { **push**  |  **pop** } **)**

## <a name="options"></a>選項

**精確** | 嚴格, 但不包括, 在關閉時推送 |   | \
指定浮點行為, 其可以是**精確**、**嚴格**或**except**。 如需詳細資訊，請參閱 [/fp (指定浮點行為)](../build/reference/fp-specify-floating-point-behavior.md)。 設定可以是 [**開啟**] 或 [**關閉**]。

當**strict**時, [**開啟**] 或 [**關閉**] 設定會指定**strict**和**except**的設定。 **除了**[**精確**] 或 [**嚴格**] 也設定為 [**開啟**] 時, [只能] 設定為 [**開啟**]。

如果新增了選擇性的**推送**token, 則**float_control**的目前設定會推送至內部編譯器堆疊。

**式**\
將目前的**float_control**設定推送至內部編譯器堆疊

**提示**\
從內部編譯器堆疊的頂端移除**float_control**設定, 並使其成為新的**float_control**設定。

## <a name="remarks"></a>備註

**除了 on 以外**, 您無法使用**float_control**來關閉**精確**的。 同樣地, 當[fenv_access](../preprocessor/fenv-access.md)為 on 時, 就無法關閉**精確**。 若要使用**float_control** pragma 從 strict 模型移至快速模型, 請使用下列程式碼:

```cpp
#pragma float_control(except, off)
#pragma fenv_access(off)
#pragma float_control(precise, off)
```

若要使用**float_control** pragma 從快速模型移至 strict 模型, 請使用下列程式碼:

```cpp
#pragma float_control(precise, on)
#pragma fenv_access(on)
#pragma float_control(except, on)
```

如果未指定任何選項, **float_control**就不會有任何作用。

其他浮點 pragma 包括：

- [fenv_access](../preprocessor/fenv-access.md)

- [fp_contract](../preprocessor/fp-contract.md)

## <a name="example"></a>範例

下列範例示範如何使用 pragma **float_control**來攔截溢位的浮點例外狀況。

```cpp
// pragma_directive_float_control.cpp
// compile with: /EHa
#include <stdio.h>
#include <float.h>

double func( ) {
   return 1.1e75;
}

#pragma float_control (except, on)

int main( ) {
   float u[1];
   unsigned int currentControl;
   errno_t err;

   err = _controlfp_s(&currentControl, ~_EM_OVERFLOW, _MCW_EM);
   if (err != 0)
      printf_s("_controlfp_s failed!\n");

   try  {
      u[0] = func();
      printf_s ("Fail");
      return(1);
   }

   catch (...)  {
      printf_s ("Pass");
      return(0);
   }
}
```

```Output
Pass
```

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
