---
title: __debugbreak
ms.date: 09/02/2019
f1_keywords:
- __debugbreak_cpp
- __debugbreak
helpviewer_keywords:
- breakpoints, __debugbreak intrinsic
- __debugbreak intrinsic
ms.assetid: 1d1e1c0c-891a-4613-ae4b-d790094ba830
ms.openlocfilehash: e4cf2c85818a878417c560ddb5a80f8690e60a93
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217931"
---
# <a name="__debugbreak"></a>__debugbreak

**Microsoft 專屬**

在您的程式碼中導致中斷點，在該位置，系統會提示使用者執行偵錯工具。

## <a name="syntax"></a>語法

```C
void __debugbreak();
```

## <a name="requirements"></a>需求

|內建|架構|標頭|
|---------------|------------------|------------|
|`__debugbreak`|x86、x64、ARM、ARM64|\<intrin.h>|

## <a name="remarks"></a>備註

編譯器內建函式類似于 [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak)，是可移植的 Win32 方法，以造成中斷點。`__debugbreak`

> [!NOTE]
> 以 **/clr**進行編譯時，包含`__debugbreak`的函式會編譯為 MSIL。 `asm int 3` 會導致函式編譯為原生。 如需詳細資訊，請參閱[__asm](../assembler/inline/asm.md)。

例如：

```C
main() {
   __debugbreak();
}
```

類似於：

```C
main() {
   __asm {
      int 3
   }
}
```

(在 x86 電腦上)。

在 ARM64 上， `__debugbreak`內建函式會編譯成指令`brk #0xF000`。

此常式僅可作為內建常式使用。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)\
[關鍵字](../cpp/keywords-cpp.md)
