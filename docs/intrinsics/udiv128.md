---
title: _udiv128
ms.date: 04/17/2019
f1_keywords:
- _udiv128
helpviewer_keywords:
- _udiv128 intrinsic
ms.openlocfilehash: 5e8cc9ca3dbf19a04d07edb1d73df84f2e29a5c3
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857979"
---
# <a name="_udiv128"></a>_udiv128

`_udiv128` 內建會以64位不帶正負號的整數除以128位不帶正負號的整數。 傳回值會保存商，而內建會透過指標參數傳回餘數。 `_udiv128` 是**Microsoft 特有**的。

## <a name="syntax"></a>語法

```C
unsigned __int64 _udiv128(
   unsigned __int64 highDividend,
   unsigned __int64 lowDividend,
   unsigned __int64 divisor,
   unsigned __int64 *remainder
);
```

### <a name="parameters"></a>參數

*highDividend* \
在被除數的高64位。

*lowDividend* \
在被除數的低64位。

*除數* \
在要除以的64位整數。

*餘數* \
脫銷餘數的64位整數位。

## <a name="return-value"></a>傳回值

商的64位。

## <a name="remarks"></a>備註

在*highDividend*中傳遞128位的64位，以及*lowDividend*中較低的64位。 內建函式會將此值除以*除數*。 它會將餘數儲存在*餘數*所指向的64位不帶正負號整數中，並傳回商的64位。

從 Visual Studio 2019 RTM 開始提供 `_udiv128` 內建。

## <a name="requirements"></a>需求

|內建|架構|標頭|
|---------------|------------------|------------|
|`_udiv128`|x64|\<immintrin.h>. h >|

## <a name="see-also"></a>請參閱

[_div128](div128.md) \
[編譯器內建函式](compiler-intrinsics.md)
