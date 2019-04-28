---
title: __ll_rshift
ms.date: 11/04/2016
f1_keywords:
- __ll_rshift_cpp
- __ll_rshift
helpviewer_keywords:
- __ll_rshift intrinsic
- ll_rshift intrinsic
ms.assetid: ef13b732-d122-44a0-add9-f5544a2c4ab2
ms.openlocfilehash: e39f8fe797467569077dd24baf49670607915107
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62263356"
---
# <a name="llrshift"></a>__ll_rshift

**Microsoft 專屬**

將第二個參數所指定的位元數右邊的第一個參數所指定的 64 位元值。

## <a name="syntax"></a>語法

```
__int64 __ll_rshift(
   __int64 Mask,
   int nBit
);
```

#### <a name="parameters"></a>參數

*遮罩*<br/>
[in]要向右移位的 64 位元整數值。

*nBit*<br/>
[in]模數 64，在 x64 上，並在 x86 上的 32 模數移位的位元數。

## <a name="return-value"></a>傳回值

遮罩移位`nBit`位元。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__ll_rshift`|x86、x64|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

如果第二個參數是否大於 64 (在 x86 上的 32) 在 x64 上，該數字會採取模數 64 (在 x86 上的 32)，以判斷要移位的位元數。 `ll`前置詞會指示這是作業，在`long long`、 另一個名稱`__int64`，64 位元帶正負號的整數類資料類型。

## <a name="example"></a>範例

```
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

## <a name="output"></a>Output

```
ffffffffffffff00
- 100
fffffffffffffff0
- 10
```

**附註**如果`_ull_rshift`已被使用，向右移位值的 MSB 原本零，因此想要的結果不所取得在負值的情況下。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)<br/>
[__ll_lshift](../intrinsics/ll-lshift.md)<br/>
[__ull_rshift](../intrinsics/ull-rshift.md)