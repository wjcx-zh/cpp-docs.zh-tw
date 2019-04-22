---
title: __ll_lshift
ms.date: 11/04/2016
f1_keywords:
- __ll_lshift_cpp
- __ll_lshift
helpviewer_keywords:
- ll_lshift intrinsic
- __ll_lshift intrinsic
ms.assetid: fe98f733-426d-44b3-8f24-5d0d6d44bd94
ms.openlocfilehash: 5a91ce5db46b19be570f8d48a584a2caeabcc163
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59024461"
---
# <a name="lllshift"></a>__ll_lshift

**Microsoft 專屬**

提供的 64 位元值向左移位指定的位元數。

## <a name="syntax"></a>語法

```
unsigned __int64 __ll_lshift(
   unsigned __int64 Mask,
   int nBit
);
```

#### <a name="parameters"></a>參數

*遮罩*<br/>
[in]要向左移位的 64 位元整數值。

*nBit*<br/>
[in]要移位的位元數。

## <a name="return-value"></a>傳回值

遮罩向左旋轉`nBit`位元。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__ll_lshift`|x86、x64|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

如果您編譯您使用 64 位元架構的程式和`nBit`大於 63，移位的位元數字是`nBit`模數 64。 如果您編譯您使用 32 位元架構的程式和`nBit`大於 31，移位的位元數字是`nBit`32 模數。

`ll`名稱中指出這是作業，在`long long`(`__int64`)。

## <a name="example"></a>範例

```
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

```
10000
```

**請注意**沒有左的移位作業的不帶正負號的版本。 這是因為`__ll_lshift`已使用不帶正負號的輸入的參數。 與向右移位，沒有任何登相依性，如左移，因為結果中的最小顯著性位元一定會設定為零無論正負號的移位的值為何。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[__ll_rshift](../intrinsics/ll-rshift.md)<br/>
[__ull_rshift](../intrinsics/ull-rshift.md)<br/>
[編譯器內建](../intrinsics/compiler-intrinsics.md)