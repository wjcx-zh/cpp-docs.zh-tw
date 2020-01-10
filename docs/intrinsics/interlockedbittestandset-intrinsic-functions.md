---
title: _interlockedbittestandset 內建函式
ms.date: 09/02/2019
f1_keywords:
- _interlockedbittestandset_cpp
- _interlockedbittestandset_HLEAcquire
- _interlockedbittestandset64
- _interlockedbittestandset64_acq
- _interlockedbittestandset64_nf
- _interlockedbittestandset64_rel
- _interlockedbittestandset
- _interlockedbittestandset_rel
- _interlockedbittestandset64_HLEAcquire
- _interlockedbittestandset_HLERelease
- _interlockedbittestandset_acq
- _interlockedbittestandset_nf
- _interlockedbittestandset64_cpp
- _interlockedbittestandset64_HLERelease
helpviewer_keywords:
- _interlockedbittestandset intrinsic
- _interlockedbittestandset64 intrinsic
- lock_bts instruction
ms.assetid: b1b7e334-53ea-48cf-ba60-5fa3ef51a1fc
ms.openlocfilehash: 9679abf674b5ef366818e73504c3c8c80c5d8ed7
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217755"
---
# <a name="_interlockedbittestandset-intrinsic-functions"></a>_interlockedbittestandset 內建函式

**Microsoft 專屬**

產生指示來檢查位址`b` `a`的位, 並傳回其目前的值, 然後再將它設定為1。

## <a name="syntax"></a>語法

```C
unsigned char _interlockedbittestandset(
   long *a,
   long b
);
unsigned char _interlockedbittestandset_acq(
   long *a,
   long b
);
unsigned char _interlockedbittestandset_HLEAcquire(
   long *a,
   long b
);
unsigned char _interlockedbittestandset_HLERelease(
   long *a,
   long b
);
unsigned char _interlockedbittestandset_nf(
   long *a,
   long b
);
unsigned char _interlockedbittestandset_rel(
   long *a,
   long b
);
unsigned char _interlockedbittestandset64(
   __int64 *a,
   __int64 b
);
unsigned char _interlockedbittestandset64_acq(
   __int64 *a,
   __int64 b
);
unsigned char _interlockedbittestandset64_nf(
   __int64 *a,
   __int64 b
);
unsigned char _interlockedbittestandset64_rel(
   __int64 *a,
   __int64 b
);
unsigned char _interlockedbittestandset64_HLEAcquire(
   __int64 *a,
   __int64 b
);
unsigned char _interlockedbittestandset64_HLERelease(
   __int64 *a,
   __int64 b
);
```

### <a name="parameters"></a>參數

*為*\
在要檢查之記憶體的指標。

*位元組*\
在要測試的位位置。

## <a name="return-value"></a>傳回值

位在設定之前的位置`b`值。

## <a name="requirements"></a>需求

|內建|架構|標頭|
|---------------|------------------|------------|
|`_interlockedbittestandset`|x86、ARM、x64、ARM64|\<intrin.h>|
|`_interlockedbittestandset_acq`、`_interlockedbittestandset_nf`、`_interlockedbittestandset_rel`|ARM、ARM64|\<intrin.h>|
|`_interlockedbittestandset64_acq`、`_interlockedbittestandset64_nf`、`_interlockedbittestandset64_rel`|ARM64|\<intrin.h>|
|`_interlockedbittestandset_HLEAcquire`、 `_interlockedbittestandset_HLERelease`|x86、x64|\<immintrin.h>|
|`_interlockedbittestandset64`|x64、ARM64|\<intrin.h>|
|`_interlockedbittestandset64_HLEAcquire`、 `_interlockedbittestandset64_HLERelease`|X64|\<immintrin.h>|

## <a name="remarks"></a>備註

在 x86 和 x64 處理器上, 這些內建函式`lock bts`會使用指令來讀取並將指定的位設定為1。 此作業是不可部分完成的。

在 ARM 和 ARM64 處理器上, 針對取得和`_acq`發行`_rel`語義使用具有和後置詞的內建函式, 例如在重要區段的開頭和結尾。 具有`_nf` (「無範圍」) 尾碼的 ARM 內建函式不會做為記憶體屏障。

在支援 Hardware Lock Elision (HLE) 指令的 Intel 處理器上，搭配 `_HLEAcquire` 和 `_HLERelease` 字尾的內建函式會包含對處理器的提示，提示其可以藉由消除硬體中鎖定寫入 (lock write) 的階段以加速效能。 如果在不支援 HLE 的處理器上呼叫這些內建函式, 則會忽略提示。

這些常式僅以內建函式的形式供您使用。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)\
[與 x86 編譯器衝突](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)
