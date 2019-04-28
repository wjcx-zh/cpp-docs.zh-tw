---
title: _interlockedbittestandreset 內建函式
ms.date: 12/17/2018
f1_keywords:
- _interlockedbittestandreset_rel
- _interlockedbittestandreset64
- _interlockedbittestandreset64_HLERelease
- _interlockedbittestandreset_HLERelease
- _interlockedbittestandreset_HLEAcquire
- _interlockedbittestandreset_acq
- _interlockedbittestandreset_cpp
- _interlockedbittestandreset_nf
- _interlockedbittestandreset64_cpp
- _interlockedbittestandreset64_HLEAcquire
- _interlockedbittestandreset
helpviewer_keywords:
- lock_btr instruction
- _interlockedbittestandreset64 intrinsic
- _interlockedbittestandreset intrinsic
ms.assetid: 9bbb1442-f2e9-4dc2-b0da-97f3de3493b9
ms.openlocfilehash: 54ea8b1ccac15eab600c91302969b606c188dc59
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62263720"
---
# <a name="interlockedbittestandreset-intrinsic-functions"></a>_interlockedbittestandreset 內建函式

**Microsoft 專屬**

產生指令，可將位址 `b` 的位元 `a` 設定為零，並傳回其原始值。

## <a name="syntax"></a>語法

```
unsigned char _interlockedbittestandreset(
   long *a,
   long b
);
unsigned char _interlockedbittestandreset_acq(
   long *a,
   long b
);
unsigned char _interlockedbittestandreset_HLEAcquire(
   long *a,
   long b
);
unsigned char _interlockedbittestandreset_HLERelease(
   long *a,
   long b
);
unsigned char _interlockedbittestandreset_nf(
   long *a,
   long b
);
unsigned char _interlockedbittestandreset_rel(
   long *a,
   long b
);
unsigned char _interlockedbittestandreset64(
   __int64 *a,
   __int64 b
);
unsigned char _interlockedbittestandreset64_HLEAcquire(
   __int64 *a,
   __int64 b
);
unsigned char _interlockedbittestandreset64_HLERelease(
   __int64 *a,
   __int64 b
);
```

#### <a name="parameters"></a>參數

*a*<br/>
[in]要檢查的記憶體指標。

*b*<br/>
[in]要測試的位元位置。

## <a name="return-value"></a>傳回值

`b` 所指定位置上的位元之原始值。

## <a name="requirements"></a>需求

|內建|架構|標頭|
|---------------|------------------|------------|
|`_interlockedbittestandreset`|x86、 x64、 ARM|\<intrin.h>|
|`_interlockedbittestandreset_acq`、`_interlockedbittestandreset_nf`、`_interlockedbittestandreset_rel`|ARM|\<intrin.h>|
|`_interlockedbittestandreset_HLEAcquire`、 `_interlockedbittestandreset_HLERelease`|x86、x64|\<immintrin.h>|
|`_interlockedbittestandreset64`|X64|\<intrin.h>|
|`_interlockedbittestandreset64_HLEAcquire`、 `_interlockedbittestandreset64_HLERelease`|X64|\<immintrin.h>|

## <a name="remarks"></a>備註

在 x86 和 x64 處理器上使用這些內建函式`lock btr`指令，讀取，並在不可部分完成的作業中設定指定的位元設為零。

在 ARM 處理器上，搭配取得和釋放語意的 `_acq` 和 `_rel` 字尾使用內建函式，例如在重要區段的開頭和結尾處。 搭配 `_nf` (「無範圍」) 字尾的 ARM 內建函式不會當做記憶體屏障。

在支援 Hardware Lock Elision (HLE) 指令的 Intel 處理器上，搭配 `_HLEAcquire` 和 `_HLERelease` 字尾的內建函式會包含對處理器的提示，提示其可以藉由消除硬體中鎖定寫入 (lock write) 的階段以加速效能。 如果這些內建函式在不支援 HLE 的處理器上被呼叫，則會忽略提示。

這些常式僅以內建函式的形式供您使用。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)<br/>
[與 x86 編譯器衝突](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)