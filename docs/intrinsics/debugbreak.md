---
title: __debugbreak
ms.date: 11/04/2016
f1_keywords:
- __debugbreak_cpp
- __debugbreak
helpviewer_keywords:
- breakpoints, __debugbreak intrinsic
- __debugbreak intrinsic
ms.assetid: 1d1e1c0c-891a-4613-ae4b-d790094ba830
ms.openlocfilehash: b52c34014402a235e03c45f82dcd1e5c542e4919
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59023096"
---
# <a name="debugbreak"></a>__debugbreak

**Microsoft 特定的**

在您的程式碼中導致中斷點，在該位置，系統會提示使用者執行偵錯工具。

## <a name="syntax"></a>語法

```
void __debugbreak();
```

## <a name="requirements"></a>需求

|內建|架構|標頭|
|---------------|------------------|------------|
|`__debugbreak`|x86、 x64、 ARM|\<intrin.h>|

## <a name="remarks"></a>備註

`__debugbreak`編譯器內建函式，類似於[DebugBreak](https://msdn.microsoft.com/library/windows/desktop/ms679297.aspx)，是能造成中斷點的可移植 Win32 方式。

> [!NOTE]
>  進行編譯時 **/clr**，函式，包含`__debugbreak`會編譯為 MSIL。 `asm int 3` 會導致編譯成原生函式。 如需詳細資訊，請參閱 < [__asm](../assembler/inline/asm.md)。

例如: 

```
main() {
   __debugbreak();
}
```

類似於：

```
main() {
   __asm {
      int 3
   }
}
```

(在 x86 電腦上)。

此常式僅可作為內建常式使用。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)