---
title: _BitScanReverse, _BitScanReverse64
ms.date: 11/04/2016
f1_keywords:
- _BitScanReverse64
- _BitScanReverse_cpp
- _BitScanReverse
- _BitScanReverse64_cpp
helpviewer_keywords:
- bsr instruction
- _BitScanReverse intrinsic
- BitScanReverse intrinsic
ms.assetid: 2520a207-af8b-4aad-9ae7-831abeadf376
ms.openlocfilehash: f1c33f90fc8e44388068f0588d33effd80fc203c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50586416"
---
# <a name="bitscanreverse-bitscanreverse64"></a>_BitScanReverse, _BitScanReverse64

**Microsoft 專屬**

從遮罩資料的最高有效位元 (MSB) 到最低有效位元 (LSB) 搜尋設定位元 (1)。

## <a name="syntax"></a>語法

```
unsigned char _BitScanReverse(
   unsigned long * Index,
   unsigned long Mask
);
unsigned char _BitScanReverse64(
   unsigned long * Index,
   unsigned __int64 Mask
);
```

#### <a name="parameters"></a>參數

*Tuple*<br/>
[out]會使用找到的第一個設定位元 (1) 的位元位置載入。

*遮罩*<br/>
[in]要搜尋的 32 位元或 64 位元值。

## <a name="return-value"></a>傳回值

如果已設定 `Index` 則為非零，如果找不到設定位元則為 0。

## <a name="requirements"></a>需求

|內建|架構|頁首|
|---------------|------------------|------------|
|`_BitScanReverse`|x86、 x64、 ARM|\<intrin.h>|
|`_BitScanReverse64`|ARM、 x64||

## <a name="example"></a>範例

```
// BitScanReverse.cpp
// compile with: /EHsc
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(_BitScanReverse)

int main()
{
   unsigned long mask = 0x1000;
   unsigned long index;
   unsigned char isNonzero;

   cout << "Enter a positive integer as the mask: " << flush;
   cin >> mask;
   isNonzero = _BitScanReverse(&index, mask);
   if (isNonzero)
   {
      cout << "Mask: " << mask << " Index: " << index << endl;
   }
   else
   {
      cout << "No set bits found.  Mask is zero." << endl;
   }
}
```

## <a name="input"></a>輸入

```
12
```

## <a name="sample-output"></a>範例輸出

```
Enter a positive integer as the mask:
Mask: 12 Index: 3
```

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)