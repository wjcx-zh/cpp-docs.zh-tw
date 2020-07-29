---
title: __ll_rshift
ms.date: 09/02/2019
f1_keywords:
- __ll_rshift_cpp
- __ll_rshift
helpviewer_keywords:
- __ll_rshift intrinsic
- ll_rshift intrinsic
ms.assetid: ef13b732-d122-44a0-add9-f5544a2c4ab2
ms.openlocfilehash: 6ae750f1a8825096ee30adb01768d5603ab23a01
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219660"
---
# <a name="__ll_rshift"></a>__ll_rshift

**Microsoft 特定的**

以第二個參數所指定的位數，將第一個參數指定的64位值向右移位。

## <a name="syntax"></a>語法

```C
__int64 __ll_rshift(
   __int64 Mask,
   int nBit
);
```

### <a name="parameters"></a>參數

*遮罩*\
在要右移的64位整數值。

*nBit*\
在要移位的位數、x64 上的模數64和 x86 上的模數32。

## <a name="return-value"></a>傳回值

以位移位的遮罩 `nBit` 。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__ll_rshift`|x86、x64|

**標頭檔** \<intrin.h>

## <a name="remarks"></a>備註

如果第二個參數在 x64 （x86 上為32）上大於64，則會採用模數64（x86 上的32）來判斷要移位的位數。 `ll`前置詞表示它是的作業 **`long long`** ，另一個名稱為 **`__int64`** ，64位帶正負號的整數類資料類型。

## <a name="example"></a>範例

```cpp
// ll_rshift.cpp
// compile with: /EHsc
// processor: x86, x64
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(__ll_rshift)

int main()
{
   __int64 Mask = - 0x100;
   int nBit = 4;
   cout << hex << Mask << endl;
   cout << " - " << (- Mask) << endl;
   Mask = __ll_rshift(Mask, nBit);
   cout << hex << Mask << endl;
   cout << " - " << (- Mask) << endl;
}
```

## <a name="output"></a>輸出

```Output
ffffffffffffff00
- 100
fffffffffffffff0
- 10
```

> [!NOTE]
> 如果已 `_ull_rshift` 使用，則右移值的 MSB 會是零，因此不會在負數值的情況下取得所需的結果。

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)\
[__ll_lshift](../intrinsics/ll-lshift.md)\
[__ull_rshift](../intrinsics/ull-rshift.md)
