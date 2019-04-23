---
title: _udiv64
ms.date: 04/17/2019
f1_keywords:
- _udiv64
helpviewer_keywords:
- _udiv64 intrinsic
ms.openlocfilehash: 73a29b180eeda49a9a25e9e568d25c7563234fad
ms.sourcegitcommit: 2ce88de75e7681220ae09a0ab13056f22f357a46
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "59982447"
---
# <a name="udiv64"></a>_udiv64

`_udiv64`內建函式會將由 32 位元不帶正負號的整數的 64 位元不帶正負號的整數。 傳回值包含商數和內建函式會傳回透過指標參數的餘數。 `_udiv64` 已**Microsoft 專有**。

## <a name="syntax"></a>語法

```C
unsigned int _udiv64(
   unsigned __int64 dividend,
   unsigned int divisor,
   unsigned int* remainder
);
```

### <a name="parameters"></a>參數

*dividend*<br/>
[in]要除以的 64 位元不帶正負號的整數。

*divisor*<br/>
[in]要除以的 32 位元不帶正負號的整數。

*remainder*<br/>
[out]32 位元不帶正負號的整數餘數。

## <a name="return-value"></a>傳回值

商數的 32 位元。

## <a name="remarks"></a>備註

`_udiv64`內建除以*被除數*依*除數*。 它將餘數儲存在所指的 32 位元不帶正負號整數*餘數*，並傳回商數的 32 位元。

`_udiv64`內建函式是在 Visual Studio 2019 RTM 起可用。

## <a name="requirements"></a>需求

|內建|架構|標頭|
|---------------|------------------|------------|
|`_udiv64`|x86、x64|\<immintrin.h>|

## <a name="see-also"></a>另請參閱

[_div64](div64.md) \
[編譯器內建函式](compiler-intrinsics.md)
