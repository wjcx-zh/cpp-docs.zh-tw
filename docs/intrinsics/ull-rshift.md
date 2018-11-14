---
title: __ull_rshift
ms.date: 11/04/2016
f1_keywords:
- __ull_rshift
helpviewer_keywords:
- ull_rshift intrinsic
- __ull_rshift intrinsic
ms.assetid: b7ff5254-3540-4e6e-b57c-a6c4beb7dca2
ms.openlocfilehash: 940e1e3a957b44f0aaa225f7fc9e107926ba879f
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51330498"
---
# <a name="ullrshift"></a>__ull_rshift

**Microsoft 專屬**

在 x64 上，將第二個參數所指定的位元數右邊的第一個參數所指定的 64 位元值。

## <a name="syntax"></a>語法

```
unsigned __int64 __ull_rshift(
   unsigned __int64 mask, 
   int nBit
);
```

#### <a name="parameters"></a>參數

*遮罩*<br/>
[in]要向右移位的 64 位元整數值。

*nBit*<br/>
[in]若移動，請在 x86 上的 32 模數和模數 x64 的 64 位元數。

## <a name="return-value"></a>傳回值

遮罩移位`nBit`位元。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__ull_rshift`|x86、x64|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

如果第二個參數大於 31 x86 (在 x64 上為 63) 上，該數字會採取模數 32 (在 x64 上為 64)，以判斷要移位的位元數。 `ull`名稱中指出`unsigned long long (unsigned __int64)`。

## <a name="example"></a>範例

```
// ull_rshift.cpp
// compile with: /EHsc
// processor: x86, x64
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(__ull_rshift)

int main()
{
   unsigned __int64 mask = 0x100;
   int nBit = 8;
   mask = __ull_rshift(mask, nBit);
   cout << hex << mask << endl;
}
```

## <a name="output"></a>輸出

```
1
```

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[__ll_lshift](../intrinsics/ll-lshift.md)<br/>
[__ll_rshift](../intrinsics/ll-rshift.md)<br/>
[編譯器內建](../intrinsics/compiler-intrinsics.md)