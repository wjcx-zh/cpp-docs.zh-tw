---
title: _InterlockedAddLargeStatistic
ms.date: 11/04/2016
f1_keywords:
- _InterlockedAddLargeStatistic
- _InterlockedAddLargeStatistic_cpp
helpviewer_keywords:
- _InterlockedAddLargeStatistic intrinsic
- InterlockedAddLargeStatistic intrinsic
ms.assetid: 2802e74b-bcee-46e4-b562-894908d44409
ms.openlocfilehash: befcd74c432eb62ab3a718223ada6d0f441e72c0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432821"
---
# <a name="interlockedaddlargestatistic"></a>_InterlockedAddLargeStatistic

**Microsoft 專屬**

執行連鎖的相加的第一個運算元的 64 位元值。

## <a name="syntax"></a>語法

```
long _InterlockedAddLargeStatistic(
   __int64 volatile * Addend,
   long Value
);
```

#### <a name="parameters"></a>參數

*加數*<br/>
[in、 out]新增作業的第一個運算元指標。 指向的值會由相加的結果取代。

*值*<br/>
[in]第二個運算元中;要新增的第一個運算元的值。

## <a name="return-value"></a>傳回值

第二個運算元的值。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`_InterlockedAddLargeStatistic`|x86|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

此內建函式不是不可部分完成因為它會實作為兩個不同的鎖定的指示。 不可部分完成的 64 位元讀取另一個執行緒上執行期間發生這個內建函式可能會導致不一致所讀取的值。

此函式的行為為讀寫屏障。 如需詳細資訊，請參閱 < [_ReadWriteBarrier](../intrinsics/readwritebarrier.md)。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)<br/>
[與 x86 編譯器衝突](../build/conflicts-with-the-x86-compiler.md)