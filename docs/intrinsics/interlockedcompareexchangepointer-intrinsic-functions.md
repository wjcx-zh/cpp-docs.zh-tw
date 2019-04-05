---
title: _InterlockedCompareExchangePointer 內建函式
ms.date: 11/04/2016
f1_keywords:
- _InterlockedCompareExchangePointer_HLERelease
- _InterlockedCompareExchangePointer_rel
- _InterlockedCompareExchangePointer_acq_cpp
- _InterlockedCompareExchangePointer
- _InterlockedCompareExchangePointer_cpp
- _InterlockedCompareExchangePointer_np
- _InterlockedCompareExchangePointer_rel_cpp
- _InterlockedCompareExchangePointer_HLEAcquire
- _InterlockedCompareExchangePointer_acq
- _InterlockedCompareExchangePointer_nf
helpviewer_keywords:
- InterlockedCompareExchangePointer_acq intrinsic
- _InterlockedCompareExchangePointer_rel intrinsic
- _InterlockedCompareExchangePointer_acq intrinsic
- InterlockedCompareExchangePointer_rel intrinsic
- InterlockedCompareExchangePointer intrinsic
- _InterlockedCompareExchangePointer_HLERelease intrinsic
- _InterlockedCompareExchangePointer_HLEAcquire intrinsic
- _InterlockedCompareExchangePointer intrinsic
- _InterlockedCompareExchangePointer_nf intrinsic
- _InterlockedCompareExchangePointer_np intrinsic
ms.assetid: 97fde59d-2bf9-42aa-a0fe-a5b6befdd44b
ms.openlocfilehash: 2db18c73f7765454d29e2dfdbd9408f62c51d32a
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59024812"
---
# <a name="interlockedcompareexchangepointer-intrinsic-functions"></a>_InterlockedCompareExchangePointer 內建函式

**Microsoft 特定的**

如果 `Exchange` 與 `Destination` 相等，則執行不可部分完成作業，可將 `Comparand` 位址儲存在 `Destination` 位址中。

## <a name="syntax"></a>語法

```
void * _InterlockedCompareExchangePointer (
   void * volatile * Destination,
   void * Exchange,
   void * Comparand
);
void * _InterlockedCompareExchangePointer_acq (
   void * volatile * Destination,
   void * Exchange,
   void * Comparand
);
void * _InterlockedCompareExchangePointer_HLEAcquire (
   void * volatile * Destination,
   void * Exchange,
   void * Comparand
);
void * _InterlockedCompareExchangePointer_HLERelease (
   void * volatile * Destination,
   void * Exchange,
   void * Comparand
);
void * _InterlockedCompareExchangePointer_nf (
   void * volatile * Destination,
   void * Exchange,
   void * Comparand
);
void * _InterlockedCompareExchangePointer_np (
   void * volatile * Destination,
   void * Exchange,
   void * Comparand
);
long _InterlockedCompareExchangePointer_rel (
   void * volatile * Destination,
   void * Exchange,
   void * Comparand
);
```

#### <a name="parameters"></a>參數

*目的地*<br/>
[in、 out]指向目的地值的指標。 會忽略正負號。

*Exchange*<br/>
[in]交換指標。 會忽略正負號。

*比較元*<br/>
[in]比較目的地的指標。 會忽略正負號。

## <a name="return-value"></a>傳回值

傳回值是目的地的初始值。

## <a name="requirements"></a>需求

|內建|架構|標頭|
|---------------|------------------|------------|
|`_InterlockedCompareExchangePointer`|x86、 x64、 ARM|\<intrin.h>|
|`_InterlockedCompareExchangePointer_acq`中， `_InterlockedCompareExchangePointer_nf`中， `_InterlockedCompareExchangePointer_rel`|ARM|\<iiintrin.h>|
|`_InterlockedCompareExchangePointer_HLEAcquire`, `_InterlockedCompareExchangePointer_HLERelease`|x86、x64|\<immintrin.h>|

## <a name="remarks"></a>備註

`_InterlockedCompareExchangePointer` 執行不可部分完成的比較`Destination`解決`Comparand`位址。 如果 `Destination` 位址等於 `Comparand` 位址，`Exchange` 位址會儲存在 `Destination` 所指定的位址中。 否則，不會執行任何作業。

`_InterlockedCompareExchangePointer` 提供 Win32 Windows SDK 的編譯器內建支援[_InterlockedCompareExchangePointer](https://msdn.microsoft.com/library/ff547863.aspx)函式。

如需如何使用的範例`_InterlockedCompareExchangePointer`，請參閱 < [_InterlockedDecrement](../intrinsics/interlockeddecrement-intrinsic-functions.md)。

在 ARM 平台上，如果您需要取得並發行語意 (例如在關鍵區段的開頭和結尾)，請使用具有 `_acq` 和 `_rel` 後置字元的內建函式。 具有 `_nf` (「沒有圍牆」) 後置字元的 ARM 內建函式不做為記憶體屏障。

搭配 `_np` (「不預先擷取」) 字尾使用內建函式，可避免編譯器插入可能的預先提取作業。

在支援 Hardware Lock Elision (HLE) 指令的 Intel 平台上，搭配 `_HLEAcquire` 和 `_HLERelease` 字尾的內建函式會包含對處理器的提示，提示其可以藉由消除硬體中鎖定寫入 (lock write) 的階段以加速效能。 如果在不支援 HLE 的平台上呼叫這些內建函式，會忽略該提示。

這些常式僅以內建函式的形式供您使用。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)