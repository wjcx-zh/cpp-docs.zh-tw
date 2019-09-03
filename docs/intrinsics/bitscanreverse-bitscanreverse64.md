---
title: _BitScanReverse, _BitScanReverse64
ms.date: 09/02/2019
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
ms.openlocfilehash: 848c153967e5581f08f1d499a28ab282ee2602df
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216953"
---
# <a name="_bitscanreverse-_bitscanreverse64"></a>_BitScanReverse, _BitScanReverse64

**Microsoft 專屬**

從遮罩資料的最高有效位元 (MSB) 到最低有效位元 (LSB) 搜尋設定位元 (1)。

## <a name="syntax"></a>語法

```C
unsigned char _BitScanReverse(
   unsigned long * Index,
   unsigned long Mask
);
unsigned char _BitScanReverse64(
   unsigned long * Index,
   unsigned __int64 Mask
);
```

### <a name="parameters"></a>參數

*指數*\
脫銷已載入第一個設定位 (1) 的位位置。

*遮罩*\
在要搜尋的32位或64位值。

## <a name="return-value"></a>傳回值

如果已設定 `Index` 則為非零，如果找不到設定位元則為 0。

## <a name="requirements"></a>需求

|內建|架構|標頭|
|---------------|------------------|------------|
|`_BitScanReverse`|x86、ARM、x64、ARM64|\<intrin.h>|
|`_BitScanReverse64`|ARM64, x64|\<intrin.h>|

## <a name="example"></a>範例

```cpp
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

```Input
12
```

```Output
Enter a positive integer as the mask:
Mask: 12 Index: 3
```

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
