---
title: _InterlockedExchange 內建函式
ms.date: 12/17/2018
f1_keywords:
- _InterlockedExchange_rel
- _InterlockedExchange8_nf
- _InterlockedExchange_acq_cpp
- _InterlockedExchange_nf
- _InterlockedExchange64_nf
- _InterlockedExchange_HLEAcquire
- _InterlockedExchange_cpp
- _InterlockedExchange64_acq_cpp
- _InterlockedExchange64_acq
- _InterlockedExchange64_HLERelease
- _InterlockedExchange8_acq
- _InterlockedExchange16_acq
- _InterlockedExchange
- _InterlockedExchange64_HLEAcquire
- _InterlockedExchange8
- _InterlockedExchange64_rel
- _InterlockedExchange_acq
- _InterlockedExchange16
- _InterlockedExchange16_rel
- _InterlockedExchange16_nf
- _InterlockedExchange64
- _InterlockedExchange_HLERelease
- _InterlockedExchange64_cpp
- _InterlockedExchange8_rel
helpviewer_keywords:
- _InterlockedExchange8
- _InterlockedExchange64 intrinsic
- _InterlockedExchange_acq intrinsic
- InterlockedExchange64 intrinsic
- _InterlockedExchange64_acq intrinsic
- InterlockedExchange64_acq intrinsic
- _InterlockedExchange16_acq
- _InterlockedExchange8_acq
- _InterlockedExchange16
- _InterlockedExchange8_rel
- InterlockedExchange_acq intrinsic
- InterlockedExchange intrinsic
- _InterlockedExchange16_rel
- _InterlockedExchange16_nf
- _InterlockedExchange intrinsic
- _InterlockedExchange8_nf
ms.assetid: be2f232a-6301-462a-a92b-fcdeb8b0f209
ms.openlocfilehash: c96ce57854bfb3eea0e1b8bc6283984c7fce50f9
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509399"
---
# <a name="_interlockedexchange-intrinsic-functions"></a>_InterlockedExchange 內建函式

**Microsoft 專屬**

會產生不可部分完成的指示，以設定指定的值。

## <a name="syntax"></a>語法

```
long _InterlockedExchange(
   long volatile * Target,
   long Value
);
long _InterlockedExchange_acq(
   long volatile * Target,
   long Value
);
long _InterlockedExchange_HLEAcquire(
   long volatile * Target,
   long Value
);
long _InterlockedExchange_HLERelease(
   long volatile * Target,
   long Value
);
long _InterlockedExchange_nf(
   long volatile * Target,
   long Value
);
long _InterlockedExchange_rel(
   long volatile * Target,
   long Value
);
char _InterlockedExchange8(
   char volatile * Target,
   char Value
);
char _InterlockedExchange8_acq(
   char volatile * Target,
   char Value
);
char _InterlockedExchange8_nf(
   char volatile * Target,
   char Value
);
char _InterlockedExchange8_rel(
   char volatile * Target,
   char Value
);
short _InterlockedExchange16(
   short volatile * Target,
   short Value
);
short _InterlockedExchange16_acq(
   short volatile * Target,
   short Value
);
short _InterlockedExchange16_nf(
   short volatile * Target,
   short Value
);
short _InterlockedExchange16_rel(
   short volatile * Target,
   short Value
);
__int64 _InterlockedExchange64(
   __int64 volatile * Target,
   __int64 Value
);
__int64 _InterlockedExchange64_acq(
   __int64 volatile * Target,
   __int64 Value
);
__int64 _InterlockedExchange64_HLEAcquire(
   __int64 volatile * Target,
   __int64 Value
);
__int64 _InterlockedExchange64_HLERelease(
   __int64 volatile * Target,
   __int64 Value
);
__int64 _InterlockedExchange64_nf(
   __int64 volatile * Target,
   __int64 Value
);
__int64 _InterlockedExchange64_rel(
   __int64 volatile * Target,
   __int64 Value
);
```

#### <a name="parameters"></a>參數

*Target*<br/>
[in、out]要交換之值的指標。 函式會將此變數設定為 `Value`，並傳回其先前的值。

*值*<br/>
在要與所指向`Target`的值交換的值。

## <a name="return-value"></a>傳回值

傳回 `Target` 所指的初始值。

## <a name="requirements"></a>需求

|內建|架構|標頭|
|---------------|------------------|------------|
|`_InterlockedExchange`, `_InterlockedExchange8`, `_InterlockedExchange16`, `_InterlockedExchange64`|x86、ARM、x64|\<intrin.h>|
|`_InterlockedExchange_acq`、`_InterlockedExchange_nf`、`_InterlockedExchange_rel`、`_InterlockedExchange8_acq`、`_InterlockedExchange8_nf`、`_InterlockedExchange8_rel`、`_InterlockedExchange16_acq`、`_InterlockedExchange16_nf`、`_InterlockedExchange16_rel`、`_InterlockedExchange64_acq`、`_InterlockedExchange64_nf`、`_InterlockedExchange64_rel`、|ARM|\<intrin.h>|
|`_InterlockedExchange_HLEAcquire`, `_InterlockedExchange_HLERelease`, `_InterlockedExchange64_HLEAcquire`, `_InterlockedExchange64_HLERelease`|x86、x64|\<immintrin.h>|

## <a name="remarks"></a>備註

`_InterlockedExchange`為 Win32 Windows SDK [InterlockedExchange](/windows/win32/api/winnt/nf-winnt-interlockedexchange)函數提供編譯器內建支援。

在 `_InterlockedExchange` 上有數個變化，會因所涉及的資料類型，以及是否使用處理器專用的取得或釋放語意，而有所不同。

`_InterlockedExchange` 函式在 32 位元整數值上運算；`_InterlockedExchange8` 在 8 位元整數值上運算；`_InterlockedExchange16` 在 16 位元整數值上運算；`_InterlockedExchange64` 在 64 位元整數值上運算。

在 ARM 平台上，搭配取得和釋放語意的 `_acq` 和 `_rel` 字尾使用內建函式，例如在重要區段的開頭和結尾處。 搭配 `_nf` (「無範圍」) 字尾的內建函式，不會當做記憶體屏障。

在支援 Hardware Lock Elision (HLE) 指令的 Intel 平台上，搭配 `_HLEAcquire` 和 `_HLERelease` 字尾的內建函式會包含對處理器的提示，提示其可以藉由消除硬體中鎖定寫入 (lock write) 的階段以加速效能。 如果在不支援 HLE 的平台上呼叫這些內建函式，會忽略該提示。

這些常式僅以內建函式的形式供您使用。

## <a name="example"></a>範例

如需如何使用`_InterlockedExchange`的範例, 請參閱[_InterlockedDecrement](../intrinsics/interlockeddecrement-intrinsic-functions.md)。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)<br/>
[與 x86 編譯器衝突](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)