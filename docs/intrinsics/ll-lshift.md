---
title: __ll_lshift
ms.date: 09/02/2019
f1_keywords:
- __ll_lshift_cpp
- __ll_lshift
helpviewer_keywords:
- ll_lshift intrinsic
- __ll_lshift intrinsic
ms.assetid: fe98f733-426d-44b3-8f24-5d0d6d44bd94
ms.openlocfilehash: 158ecbf39320d70b51f1f498a0b689ba58fec363
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221818"
---
# <a name="__ll_lshift"></a>__ll_lshift

**Microsoft 專屬**

將提供的64位值向左移動指定的位數。

## <a name="syntax"></a>語法

```C
unsigned __int64 __ll_lshift(
   unsigned __int64 Mask,
   int nBit
);
```

### <a name="parameters"></a>參數

*遮罩*\
在要向左移位的64位整數值。

*nBit*\
在要移位的位數。

## <a name="return-value"></a>傳回值

遮罩會以`nBit`位左移。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__ll_lshift`|x86、x64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

如果您為64位架構編譯器, 且`nBit`大於 63, 則要移位的位數為`nBit`模數64。 如果您為32位架構編譯器, 且`nBit`大於 31, 則要移位的位數為`nBit`模數32。

名稱`ll`中的表示它是上`long long`的作業 (`__int64`)。

## <a name="example"></a>範例

```cpp
// ll_lshift.cpp
// compile with: /EHsc
// processor: x86, x64
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(__ll_lshift)

int main()
{
   unsigned __int64 Mask = 0x100;
   int nBit = 8;
   Mask = __ll_lshift(Mask, nBit);
   cout << hex << Mask << endl;
}
```

## <a name="output"></a>Output

```Output
10000
```

> [!NOTE]
> 左移作業沒有未簽署的版本。 這是因為`__ll_lshift`已經使用不帶正負號的輸入參數。 與右移位不同的是, 左邊的 shift 沒有正負號的相依性, 因為結果中的最小有效位一律會設定為零, 而不論已移動的值正負號為何。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[__ll_rshift](../intrinsics/ll-rshift.md)\
[__ull_rshift](../intrinsics/ull-rshift.md)\
[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
