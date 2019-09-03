---
title: _udiv64
ms.date: 09/02/2019
f1_keywords:
- _udiv64
helpviewer_keywords:
- _udiv64 intrinsic
ms.openlocfilehash: 6dabbc94260ef578eb1a58a1b289b4a4654decdd
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219675"
---
# <a name="_udiv64"></a>_udiv64

`_udiv64`內建會以32位不帶正負號的整數除以64位不帶正負號的整數。 傳回值會保存商, 而內建會透過指標參數傳回餘數。 `_udiv64`是**Microsoft 特有**的。

## <a name="syntax"></a>語法

```C
unsigned int _udiv64(
   unsigned __int64 dividend,
   unsigned int divisor,
   unsigned int* remainder
);
```

### <a name="parameters"></a>參數

*股利*\
在要除數的64位不帶正負號的整數。

*divisor*\
在要除以的32位不帶正負號整數。

*數量*\
脫銷32位不帶正負號的整數餘數。

## <a name="return-value"></a>傳回值

商的32位。

## <a name="remarks"></a>備註

內建函式除以*除數*。 `_udiv64` 它會將餘數儲存在*餘數*所指向的32位不帶正負號整數中, 並傳回商的32位。

從 Visual Studio 2019 RTM 開始提供內建函式。`_udiv64`

## <a name="requirements"></a>需求

|內建|架構|標頭|
|---------------|------------------|------------|
|`_udiv64`|x86、x64|\<immintrin.h>|

## <a name="see-also"></a>另請參閱

[_div64](div64.md) \
[編譯器內建函式](compiler-intrinsics.md)
