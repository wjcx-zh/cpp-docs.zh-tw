---
title: _InterlockedCompareExchange128 內建函式
ms.date: 09/02/2019
f1_keywords:
- _InterlockedCompareExchange128_cpp
- _InterlockedCompareExchange128
- _InterlockedCompareExchange128_acq
- _InterlockedCompareExchange128_nf
- _InterlockedCompareExchange128_np
- _InterlockedCompareExchange128_rel
helpviewer_keywords:
- cmpxchg16b instruction
- _InterlockedCompareExchange128 intrinsic
ms.assetid: f05918fc-716a-4f6d-b746-1456d6b96c56
ms.openlocfilehash: 525b0fd77323789eed05c47c944794ff389bfac5
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217696"
---
# <a name="_interlockedcompareexchange128-intrinsic-functions"></a>_InterlockedCompareExchange128 內建函式

**Microsoft 專屬**

執行128位連鎖比較和交換。

## <a name="syntax"></a>語法

```C
unsigned char _InterlockedCompareExchange128(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
unsigned char _InterlockedCompareExchange128_acq(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
unsigned char _InterlockedCompareExchange128_nf(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
unsigned char _InterlockedCompareExchange128_np(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
unsigned char _InterlockedCompareExchange128_rel(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
```

### <a name="parameters"></a>參數

*位置*\
[in、out]指向目的地的指標, 這是視為128位欄位的 2 64 位整數陣列。 目的地資料必須對齊16位元組, 以避免發生一般保護錯誤。

*ExchangeHigh*\
在可能與目的地的最高部分交換的64位整數。

*ExchangeLow*\
在64位的整數, 可以與目的地的低部分交換。

*ComparandResult*\
[in、out]要與目的地比較之 2 64 位整數 (視為128位欄位) 陣列的指標。  在輸出時, 會使用目的地的原始值來覆寫這個陣列。

## <a name="return-value"></a>傳回值

1, 表示128位比較元等於目的地的原始值。 `ExchangeHigh`和`ExchangeLow`會覆寫128位目的地。

如果比較元不等於目的地的原始值, 則為0。 目的地的值不變, 而比較元的值會以目的地的值覆寫。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`_InterlockedCompareExchange128`|x64、ARM64|
|`_InterlockedCompareExchange128_acq`、`_InterlockedCompareExchange128_nf`、`_InterlockedCompareExchange128_rel`|ARM64|
|`_InterlockedCompareExchange128_np`|X64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

內建會`cmpxchg16b`產生指示 (具有`lock`前置詞) 來執行128位鎖定的比較和交換。 `_InterlockedCompareExchange128` 早期版本的 AMD 64 位硬體不支援此指示。 若要檢查`cmpxchg16b`指令的硬體支援, 請使用`__cpuid` `InfoType=0x00000001 (standard function 1)`呼叫內建函式。 如果支援指令`CPUInfo[2]` , 則 (ECX) 的位13為1。

> [!NOTE]
> 一律`ComparandResult`會覆寫的值。 在`lock`指令之後, 此內建會立即將的初始值`Destination`複製`ComparandResult`到。 基於這個理由, `ComparandResult`和`Destination`應該指向不同的記憶體位置, 以避免發生非預期的行為。

雖然您可以使用`_InterlockedCompareExchange128`進行低層級的執行緒同步處理, 但如果您可以使用較小的同步處理函式 (例如其他`_InterlockedCompareExchange`內建函式), 則不需要在超過128位的情況下進行同步處理。 如果`_InterlockedCompareExchange128`您想要在記憶體中以不可部分完成的方式存取128位值, 請使用。

如果您在不支援`cmpxchg16b`指令的硬體上執行使用內建的程式碼, 結果會是無法預測的。

在 ARM 平台上，搭配取得和釋放語意的 `_acq` 和 `_rel` 字尾使用內建函式，例如在重要區段的開頭和結尾處。 具有`_nf` (「無範圍」) 尾碼的 ARM 內建函式不會做為記憶體屏障。

搭配 `_np` (「不預先擷取」) 字尾使用內建函式，可避免編譯器插入可能的預先提取作業。

此常式僅適用于內建函式。

## <a name="example"></a>範例

這個範例會`_InterlockedCompareExchange128`使用, 將 2 64 位整數陣列的最大字組取代為其最高和最低單字的總和, 並遞增低字。 `BigInt.Int`陣列的存取是不可部分完成的, 但此範例會使用單一線程, 並忽略鎖定以簡化。

```cpp
// cmpxchg16b.c
// processor: x64
// compile with: /EHsc /O2
#include <stdio.h>
#include <intrin.h>

typedef struct _LARGE_INTEGER_128 {
    __int64 Int[2];
} LARGE_INTEGER_128, *PLARGE_INTEGER_128;

volatile LARGE_INTEGER_128 BigInt;

// This AtomicOp() function atomically performs:
//   BigInt.Int[1] += BigInt.Int[0]
//   BigInt.Int[0] += 1
void AtomicOp ()
{
    LARGE_INTEGER_128 Comparand;
    Comparand.Int[0] = BigInt.Int[0];
    Comparand.Int[1] = BigInt.Int[1];
    do {
        ; // nothing
    } while (_InterlockedCompareExchange128(BigInt.Int,
                                            Comparand.Int[0] + Comparand.Int[1],
                                            Comparand.Int[0] + 1,
                                            Comparand.Int) == 0);
}

// In a real application, several threads contend for the value
// of BigInt.
// Here we focus on the compare and exchange for simplicity.
int main(void)
{
   BigInt.Int[1] = 23;
   BigInt.Int[0] = 11;
   AtomicOp();
   printf("BigInt.Int[1] = %d, BigInt.Int[0] = %d\n",
      BigInt.Int[1],BigInt.Int[0]);
}
```

```Output
BigInt.Int[1] = 34, BigInt.Int[0] = 12
```

**結束 Microsoft 專屬**


## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)\
[_InterlockedCompareExchange 內建函式](../intrinsics/interlockedcompareexchange-intrinsic-functions.md)\
[與 x86 編譯器衝突](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)
