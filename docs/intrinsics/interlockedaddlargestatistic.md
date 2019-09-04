---
title: _InterlockedAddLargeStatistic
ms.date: 09/02/2019
f1_keywords:
- _InterlockedAddLargeStatistic
- _InterlockedAddLargeStatistic_cpp
helpviewer_keywords:
- _InterlockedAddLargeStatistic intrinsic
- InterlockedAddLargeStatistic intrinsic
ms.assetid: 2802e74b-bcee-46e4-b562-894908d44409
ms.openlocfilehash: de8c5b7dfd2462dddcb98324ebacc44c8148d85e
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222083"
---
# <a name="_interlockedaddlargestatistic"></a>_InterlockedAddLargeStatistic

**Microsoft 專屬**

執行連鎖加法, 其中第一個運算元是64位的值。

## <a name="syntax"></a>語法

```C
long _InterlockedAddLargeStatistic(
   __int64 volatile * Addend,
   long Value
);
```

### <a name="parameters"></a>參數

*加數*\
[in、out]加入作業之第一個運算元的指標。 所指向的值會由加法的結果所取代。

*Value*\
在第二個運算元;要加入至第一個運算元的值。

## <a name="return-value"></a>傳回值

第二個運算元的值。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`_InterlockedAddLargeStatistic`|x86|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

`_InterlockedAddLargeStatistic`內建函式不是不可部分完成的, 因為它會實作為兩個不同的鎖定指令。 在執行內建期間于另一個執行緒上發生的不可部分完成64位讀取, 可能會導致讀取不一致的值。

`_InterlockedAddLargeStatistic`以讀寫屏障的形式運作。 如需詳細資訊, 請參閱[_ReadWriteBarrier](../intrinsics/readwritebarrier.md)。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)\
[與 x86 編譯器衝突](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)
