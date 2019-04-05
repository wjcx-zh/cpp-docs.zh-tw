---
title: _InterlockedCompareExchange128
ms.date: 11/04/2016
f1_keywords:
- _InterlockedCompareExchange128_cpp
- _InterlockedCompareExchange128
helpviewer_keywords:
- cmpxchg16b instruction
- _InterlockedCompareExchange128 intrinsic
ms.assetid: f05918fc-716a-4f6d-b746-1456d6b96c56
ms.openlocfilehash: 9330b1405ca247364cd04d3ab399f66e4f332273
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59037866"
---
# <a name="interlockedcompareexchange128"></a>_InterlockedCompareExchange128

**Microsoft 特定的**

執行 128 位元的連鎖的比較和交換。

## <a name="syntax"></a>語法

```
unsigned char _InterlockedCompareExchange128(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
```

#### <a name="parameters"></a>參數

*目的地*<br/>
[in、 out]目的地，也就是兩個 64 位元整數的陣列的指標視為 128 位元欄位。 目的地資料必須是 16 位元組對齊，以避免了一般性保護錯誤。

*ExchangeHigh*<br/>
[in]64 位元整數，可能會與目的地的較高部份交換。

*ExchangeLow*<br/>
[in]64 位元整數，可能會與目的地的低位部份交換。

*ComparandResult*<br/>
[in、 out]（視為 128 位元欄位） 的兩個 64 位元整數的陣列指標要與目的地比較。  在輸出時，這會覆寫目的地的原始值。

## <a name="return-value"></a>傳回值

1，表示 128 位元比較元等於原始值的目的地。 `ExchangeHigh` 和`ExchangeLow`覆寫的 128 位元的目的地。

如果比較元不等於目的地的原始值，0。 目的地的值不變，目的地值覆寫的比較元值。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`_InterlockedCompareExchange128`|X64|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

此內建函式會產生`cmpxchg16b`指示 (使用`lock`前置詞) 來執行的 128 位元已鎖定的比較和交換。 AMD 64 位元硬體的早期版本不支援這項指示。 若要檢查的硬體支援`cmpxchg16b`指示，請呼叫`__cpuid`內建函式與`InfoType=0x00000001 (standard function 1)`。 位元 13 的`CPUInfo[2]`(ECX) 為 1，指示是否支援。

> [!NOTE]
>  值`ComparandResult`一定會覆寫。 在後`lock`指令，此內建函式會立即將複製的初始值`Destination`至`ComparandResult`。 基於這個理由，`ComparandResult`和`Destination`應該指向不同的記憶體位置，以避免非預期的行為。

雖然您可以使用`_InterlockedCompareExchange128`針對低層級執行緒同步處理，您不需要同步處理超過 128 位元，如果您可以使用較小的同步處理函式 (例如其他`_InterlockedCompareExchange`內建函式) 改為。 使用`_InterlockedCompareExchange128`如果您想要在記憶體中的 128 位元值的不可部分完成存取。

如果您執行程式碼使用此內建在不支援的硬體上`cmpxchg16b`指令，結果會無法預測。

此常式是只提供內建函式。

## <a name="example"></a>範例

這個範例會使用`_InterlockedCompareExchange128`將兩個 64 位元整數的陣列的高位文字取代其高低字的總和，以及遞增的低位文字。 存取 BigInt.Int 陣列是不可部分完成，但此範例會使用單一執行緒，並忽略鎖定為求簡化。

```
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

**END Microsoft 特定的**

進階 Micro 裝置，inc.copyright 2007著作權所有，並保留一切權利。 進階 Micro 裝置，inc.的權限重製

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)<br/>
[_InterlockedCompareExchange 內建函式](../intrinsics/interlockedcompareexchange-intrinsic-functions.md)<br/>
[與 x86 編譯器衝突](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)