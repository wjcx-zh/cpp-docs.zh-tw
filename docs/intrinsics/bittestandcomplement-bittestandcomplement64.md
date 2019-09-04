---
title: _bittestandcomplement, _bittestandcomplement64
ms.date: 09/02/2019
f1_keywords:
- _bittestandcomplement64
- _bittestandcomplement64_cpp
- _bittestandcomplement_cpp
- _bittestandcomplement
helpviewer_keywords:
- btc instruction
- _bittestandcomplement intrinsic
- _bittestandcomplement64 intrinsic
ms.assetid: 53fa12dd-835e-4e5d-baec-a431c8678806
ms.openlocfilehash: b1dcfe86aad18c8261029c9111681e1882bc96f5
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222210"
---
# <a name="_bittestandcomplement-_bittestandcomplement64"></a>_bittestandcomplement, _bittestandcomplement64

**Microsoft 專屬**

產生的指令會檢查位址 `b` 的位元 `a`、傳回其目前值，並將位元設為它的補數。

## <a name="syntax"></a>語法

```C
unsigned char _bittestandcomplement(
   long *a,
   long b
);
unsigned char _bittestandcomplement64(
   __int64 *a,
   __int64 b
);
```

### <a name="parameters"></a>參數

*為*\
[in、out]要檢查之記憶體的指標。

*位元組*\
在要測試的位位置。

## <a name="return-value"></a>傳回值

位於指定位置的位元。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`_bittestandcomplement`|x86、ARM、x64、ARM64|
|`_bittestandcomplement64`|x64、ARM64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

此常式僅可作為內建常式使用。

## <a name="example"></a>範例

```cpp
// bittestandcomplement.cpp
// processor: x86, IPF, x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(_bittestandcomplement)
#ifdef _M_AMD64
#pragma intrinsic(_bittestandcomplement64)
#endif

int main()
{
   long i = 1;
   __int64 i64 = 0x1I64;
   unsigned char result;
   printf("Initial value: %d\n", i);
   printf("Testing bit 1\n");
   result = _bittestandcomplement(&i, 1);
   printf("Value changed to %d, Result: %d\n", i, result);
#ifdef _M_AMD64
   printf("Testing bit 0\n");
   result = _bittestandcomplement64(&i64, 0);
   printf("Value changed to %I64d, Result: %d\n", i64, result);
#endif
}
```

```Output
Initial value: 1
Testing bit 1
Value changed to 3, Result: 0
Testing bit 0
Value changed to 0, Result: 1
```

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
