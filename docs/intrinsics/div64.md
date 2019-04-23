---
title: _div64
ms.date: 04/17/2019
f1_keywords:
- _div64
helpviewer_keywords:
- _div64 intrinsic
ms.openlocfilehash: a221cc7cf0655a41873c6777aecd8a9b27131b74
ms.sourcegitcommit: 2ce88de75e7681220ae09a0ab13056f22f357a46
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "59982417"
---
# <a name="div64"></a>_div64

`_div64`內建函式會將由 32 位元整數的 64 位元的整數。 傳回值包含商數和內建函式會傳回透過指標參數的餘數。 `_div64` 已**Microsoft 專有**。

## <a name="syntax"></a>語法

```C
int _div64(
   __int64 dividend,
   int divisor,
   int* remainder
);
```

### <a name="parameters"></a>參數

*dividend* \
[in]要除以的 64 位元整數。

*divisor* \
[in]要除以的 32 位元整數。

*remainder* \
[out]32 位元整數位元的其餘部分。

## <a name="return-value"></a>傳回值

商數的 32 位元。

## <a name="remarks"></a>備註

`_div64`內建除以*被除數*依*除數*。 它將餘數儲存在所指的 32 位元整數*餘數*，並傳回商數的 32 位元。

`_div64`內建函式是在 Visual Studio 2019 RTM 起可用。

## <a name="requirements"></a>需求

|內建|架構|標頭|
|---------------|------------------|------------|
|`_div64`|x86、x64|\<immintrin.h>|

## <a name="see-also"></a>另請參閱

[_udiv64](udiv64.md) \
[編譯器內建函式](compiler-intrinsics.md)
