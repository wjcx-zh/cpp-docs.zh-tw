---
title: _InterlockedExchangePointer 內建函式
ms.date: 12/17/2018
f1_keywords:
- _InterlockedExchangePointer_cpp
- _InterlockedExchangePointer_rel
- _InterlockedExchangePointer_nf
- _InterlockedExchangePointer_HLERelease
- _InterlockedExchangePointer_acq
- _InterlockedExchangePointer
- _InterlockedExchangePointer_acq_cpp
- _InterlockedExchangePointer_HLEAcquire
helpviewer_keywords:
- _InterlockedExchangePointer_rel intrinsic
- _InterlockedExchangePointer_HLERelease intrinsic
- _InterlockedExchangePointer intrinsic
- _InterlockedExchangePointer_nf intrinsic
- _InterlockedExchangePointer_acq intrinsic
- _InterlockedExchangePointer_HLEAcquire intrinsic
- InterlockedExchangePointer_acq intrinsic
- InterlockedExchangePointer intrinsic
ms.assetid: 0eaca0b0-d79e-406b-892d-b3b462c50bbb
ms.openlocfilehash: 1f6e66ae4d5524518c3388f5af843cc15f65da50
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59024526"
---
# <a name="interlockedexchangepointer-intrinsic-functions"></a>_InterlockedExchangePointer 內建函式

**Microsoft 特定的**

執行不可部分完成的交換作業，它會將做為第二個引數傳入的位址複製到第一個引數，並傳回第一個引數的原始位址。

## <a name="syntax"></a>語法

```
void * _InterlockedExchangePointer(
   void * volatile * Target,
   void * Value
);
void * _InterlockedExchangePointer_acq(
   void * volatile * Target,
   void * Value
);
void * _InterlockedExchangePointer_rel(
   void * volatile * Target,
   void * Value
);
void * _InterlockedExchangePointer_nf(
   void * volatile * Target,
   void * Value
);
void * _InterlockedExchangePointer_HLEAcquire(
   void * volatile * Target,
   void * Value
);
void * _InterlockedExchangePointer_HLERelease(
   void * volatile * Target,
   void * Value
);
```

#### <a name="parameters"></a>參數

*Target*<br/>
[in、 out]要交換之值的指標的指標。 函式將值設定為 `Value`，並傳回其先前的值。

*值*<br/>
[in]要交換值的值所指向`Target`。

## <a name="return-value"></a>傳回值

函式會傳回 `Target` 所指向的起始值。

## <a name="requirements"></a>需求

|內建|架構|標頭|
|---------------|------------------|------------|
|`_InterlockedExchangePointer`|x86、 x64、 ARM|\<intrin.h>|
|`_InterlockedExchangePointer_acq`中， `_InterlockedExchangePointer_rel`中， `_InterlockedExchangePointer_nf`|ARM|\<intrin.h>|
|`_InterlockedExchangePointer_HLEAcquire`, `_InterlockedExchangePointer_HLERelease`|具有 HLE 支援 x64|\<immintrin.h>|

在 x86 架構上，`_InterlockedExchangePointer` 是呼叫 `_InterlockedExchange` 的巨集。

## <a name="remarks"></a>備註

在 64 位元系統上，參數為 64 個位元，而且必須在 64 位元界限上對齊；否則，函數就會失敗。 在 32 位元系統上，參數為 32 位元，而且必須在 32 位元界限上對齊。 如需詳細資訊，請參閱 <<c0> [ 對齊](../cpp/align-cpp.md)。

在 ARM 平台上，如果您需要取得並發行語意 (例如在關鍵區段的開頭和結尾)，請使用具有 `_acq` 和 `_rel` 後置字元的內建函式。 具有 `_nf` (「沒有圍牆」) 後置字元的內建函式不做為記憶體屏障。

在支援 Hardware Lock Elision (HLE) 指令的 Intel 平台上，搭配 `_HLEAcquire` 和 `_HLERelease` 字尾的內建函式會包含對處理器的提示，提示其可以藉由消除硬體中鎖定寫入 (lock write) 的階段以加速效能。 如果在不支援 HLE 的平台上呼叫這些內建函式，會忽略該提示。

這些常式僅以內建函式的形式供您使用。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)<br/>
[與 x86 編譯器衝突](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)