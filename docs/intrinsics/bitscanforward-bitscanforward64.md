---
title: _BitScanForward, _BitScanForward64
ms.date: 09/02/2019
f1_keywords:
- _BitScanForward
- _BitScanForward_cpp
- _BitScanForward64_cpp
- _BitScanForward64
helpviewer_keywords:
- _BitScanForward intrinsic
- bsf instruction
- BitScanForward intrinsic
ms.assetid: 405e60fb-0815-42a7-9b02-6fc035122203
ms.openlocfilehash: 91f43d19259419b78d1910a00a154d2d4f0adfc7
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222225"
---
# <a name="_bitscanforward-_bitscanforward64"></a>_BitScanForward, _BitScanForward64

**Microsoft 專屬**

從遮罩資料的最低有效位元 (MSB) 到最高有效位元 (LSB) 搜尋設定位元 (1)。

## <a name="syntax"></a>語法

```C
unsigned char _BitScanForward(
   unsigned long * Index,
   unsigned long Mask
);
unsigned char _BitScanForward64(
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

如果遮罩是零，則為 0；否則為非零。

## <a name="remarks"></a>備註

如果找到設定位元，會在第一個參數中傳回找到的第一個設定位元的位元位置。 如果找不到設定位元，就會傳回 0；否則，會傳回 1。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`_BitScanForward`|x86、ARM、x64、ARM64|
|`_BitScanForward64`|ARM64, x64|

**標頭檔**\<intrin.h. h >

## <a name="example"></a>範例

```cpp
// BitScanForward.cpp
// compile with: /EHsc
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(_BitScanForward)

int main()
{
   unsigned long mask = 0x1000;
   unsigned long index;
   unsigned char isNonzero;

   cout << "Enter a positive integer as the mask: " << flush;
   cin >> mask;
   isNonzero = _BitScanForward(&index, mask);
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
Mask: 12 Index: 2
```

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
