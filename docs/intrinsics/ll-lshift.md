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
ms.openlocfilehash: 988284b81c9f04ee5d7f09f8a2f173a689f9fb55
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230515"
---
# <a name="__ll_lshift"></a>__ll_lshift

**Microsoft 特定的**

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

遮罩會以位左移 `nBit` 。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__ll_lshift`|x86、x64|

**標頭檔** \<intrin.h>

## <a name="remarks"></a>備註

如果您為64位架構編譯器，且大於 `nBit` 63，則要移位的位數為 `nBit` 模數64。 如果您為32位架構編譯器，且大於 `nBit` 31，則要移位的位數為 `nBit` 模數32。

`ll`名稱中的表示它是上的作業 **`long long`** （ **`__int64`** ）。

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

## <a name="output"></a>輸出

```Output
10000
```

> [!NOTE]
> 左移作業沒有未簽署的版本。 這是因為 `__ll_lshift` 已經使用不帶正負號的輸入參數。 與右移位不同的是，左邊的 shift 沒有正負號的相依性，因為結果中的最小有效位一律會設定為零，而不論已移動的值正負號為何。

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[__ll_rshift](../intrinsics/ll-rshift.md)\
[__ull_rshift](../intrinsics/ull-rshift.md)\
[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
