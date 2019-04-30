---
title: _umul128
ms.date: 11/04/2016
f1_keywords:
- __umul128
helpviewer_keywords:
- __umul128 intrinsic
ms.assetid: 13684df3-3ac7-467c-b258-a0e93bc490b5
ms.openlocfilehash: afca1e62127ac2dbcfc407982dbe191d379b4acb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390096"
---
# <a name="umul128"></a>_umul128

**Microsoft 專屬**

將兩個作為前兩個引數傳入的 64 位元不帶正負號整數相乘，並將乘積的 64 高位元置於 `HighProduct` 所指向的 64 位元不帶正負號整數中，然後傳回乘積的 64 低位元。

## <a name="syntax"></a>語法

```
unsigned __int64 _umul128(
   unsigned __int64 Multiplier,
   unsigned __int64 Multiplicand,
   unsigned __int64 *HighProduct
);
```

#### <a name="parameters"></a>參數

*乘數*<br/>
[in]要相乘的第一個 64 位元整數。

*被乘數*<br/>
[in]要相乘的第二個 64 位元整數。

*HighProduct*<br/>
[out]高 64 個位元的產品。

## <a name="return-value"></a>傳回值

乘積的 64 低位元。

## <a name="requirements"></a>需求

|內建|架構|標頭|
|---------------|------------------|------------|
|`_umul128`|X64|\<intrin.h>|

## <a name="example"></a>範例

```
// umul128.c
// processor: x64

#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(_umul128)

int main()
{
    unsigned __int64 a = 0x0fffffffffffffffI64;
    unsigned __int64 b = 0xf0000000I64;
    unsigned __int64 c, d;

    d = _umul128(a, b, &c);

    printf_s("%#I64x * %#I64x = %#I64x%I64x\n", a, b, c, d);
}
```

```Output
0xfffffffffffffff * 0xf0000000 = 0xeffffffffffffff10000000
```

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)
