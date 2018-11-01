---
title: float_control
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.float_control
- float_control_CPP
helpviewer_keywords:
- float_control pragma
- pragmas, float_control
ms.assetid: 4f4ba5cf-3707-413e-927d-5ecdbc0a9a43
ms.openlocfilehash: 63e27e992778776e186345da07937d1a88844e5d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50611012"
---
# <a name="floatcontrol"></a>float_control

指定函式的浮點行為。

## <a name="syntax"></a>語法

> **#pragma float_control** [ **(** [*值* **，** *設定*[ **，推播**]] |[**推播** | **pop** ] **)** ]

## <a name="options"></a>選項

*值*，*設定*[，**推播**]<br/>
指定浮點行為。 *值*可以是**精確**， **strict**，或**除了**。 如需詳細資訊，請參閱 [/fp (指定浮點行為)](../build/reference/fp-specify-floating-point-behavior.md)。 *設定*可以是**上**或是**關閉**。

如果*值*是**嚴格**，兩者的設定為**嚴格**並**除了**所指定*設定*. **除了**只可以設定為**上**當**精確**或**嚴格**也會設定為**上**。

如果選擇性**推播**權杖新增，目前設定*值*推入至內部編譯器堆疊。

**push**<br/>
將目前的推送**float_control**設定至內部編譯器堆疊

**pop**<br/>
移除**float_control**設定從內部編譯器堆疊的頂端，並建立新**float_control**設定。

## <a name="remarks"></a>備註

您無法使用**float_control**來開啟**精確**關閉時**除了**上。 同樣地，**精確**無法關閉的時機[fenv_access](../preprocessor/fenv-access.md)上。 若要從 strict 模型移至 fast 模型利用**float_control** pragma，請使用下列程式碼：

```cpp
#pragma float_control(except, off)
#pragma fenv_access(off)
#pragma float_control(precise, off)
```

若要從 fast 模型移至 strict 模型**float_control** pragma，請使用下列程式碼：

```cpp
#pragma float_control(precise, on)
#pragma fenv_access(on)
#pragma float_control(except, on)
```

如果未不指定任何選項， **float_control**沒有任何作用。

其他浮點 pragma 包括：

- [fenv_access](../preprocessor/fenv-access.md)

- [fp_contract](../preprocessor/fp-contract.md)

## <a name="example"></a>範例

下列範例示範如何使用 pragma 攔截溢位浮點例外狀況**float_control**。

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

[Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
