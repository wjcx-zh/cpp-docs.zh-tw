---
title: _InterlockedExchangePointer 內建函式
ms.date: 09/02/2019
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
ms.openlocfilehash: 1402dcf5279658c1364b59a324d988129bc841d8
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217624"
---
# <a name="_interlockedexchangepointer-intrinsic-functions"></a>_InterlockedExchangePointer 內建函式

**Microsoft 專屬**

執行不可部分完成的交換作業, 將當做第二個引數傳入的位址複製到第一個引數, 並傳回第一個的原始位址。

## <a name="syntax"></a>語法

```C
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

### <a name="parameters"></a>參數

*設定*\
[in、out]要交換的值指標。 函式會將值設定為*value* , 並傳回其先前的值。

*Value*\
在要與*Target*所指向的值交換的值。

## <a name="return-value"></a>傳回值

函式會傳回*目標*所指向的初始值。

## <a name="requirements"></a>需求

|內建|架構|標頭|
|---------------|------------------|------------|
|`_InterlockedExchangePointer`|x86、ARM、x64、ARM64|\<intrin.h>|
|`_InterlockedExchangePointer_acq`、`_InterlockedExchangePointer_rel`、`_InterlockedExchangePointer_nf`|ARM、ARM64|\<intrin.h>|
|`_InterlockedExchangePointer_HLEAcquire`、 `_InterlockedExchangePointer_HLERelease`|X64|\<immintrin.h>|

在 x86 架構上，`_InterlockedExchangePointer` 是呼叫 `_InterlockedExchange` 的巨集。

## <a name="remarks"></a>備註

在64位系統上, 參數為64位, 且必須在64位界限上對齊。 否則, 函數會失敗。 在 32 位元系統上，參數為 32 位元，而且必須在 32 位元界限上對齊。 如需詳細資訊, 請參閱[align](../cpp/align-cpp.md)。

在 ARM 平台上，如果您需要取得並發行語意 (例如在關鍵區段的開頭和結尾)，請使用具有 `_acq` 和 `_rel` 後置字元的內建函式。 具有`_nf` (「無範圍」) 尾碼的內建函式不會做為記憶體屏障。

在支援 Hardware Lock Elision (HLE) 指令的 Intel 平台上，搭配 `_HLEAcquire` 和 `_HLERelease` 字尾的內建函式會包含對處理器的提示，提示其可以藉由消除硬體中鎖定寫入 (lock write) 的階段以加速效能。 如果在不支援 HLE 的平臺上呼叫這些內建函式, 則會忽略提示。

這些常式僅以內建函式的形式供您使用。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)\
[與 x86 編譯器衝突](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)
