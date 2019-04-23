---
title: _udiv128
ms.date: 04/17/2019
f1_keywords:
- _udiv128
helpviewer_keywords:
- _udiv128 intrinsic
ms.openlocfilehash: 0e66bbe978199f47134aa288bdd2bac4eb3e332a
ms.sourcegitcommit: 2ce88de75e7681220ae09a0ab13056f22f357a46
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "59982437"
---
# <a name="udiv128"></a>_udiv128

`_udiv128`內建函式會將由 64 位元不帶正負號的整數的 128 位元不帶正負號的整數。 傳回值包含商數和內建函式會傳回透過指標參數的餘數。 `_udiv128` 已**Microsoft 專有**。

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
[in]被除數高 64 個位元。

*lowDividend* \
[in]被除數低 64 個位元。

*divisor* \
[in]要除以的 64 位元整數。

*remainder* \
[out]64 位元整數位元的其餘部分。

## <a name="return-value"></a>傳回值

商數的 64 位元。

## <a name="remarks"></a>備註

傳遞的 128 位元被除數中較高的 64 位元*highDividend*，並在較低的 64 位元*lowDividend*。 內建函式會將此值乘以*除數*。 它將餘數儲存在所指的 64 位元不帶正負號整數*餘數*，並傳回商數的 64 位元。

`_udiv128`內建函式是在 Visual Studio 2019 RTM 起可用。

## <a name="requirements"></a>需求

|內建|架構|標頭|
|---------------|------------------|------------|
|`_udiv128`|X64|\<immintrin.h>|

## <a name="see-also"></a>另請參閱

[_div128](div128.md) \
[編譯器內建函式](compiler-intrinsics.md)
