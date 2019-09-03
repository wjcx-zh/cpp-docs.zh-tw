---
title: _div64
ms.date: 09/02/2019
f1_keywords:
- _div64
helpviewer_keywords:
- _div64 intrinsic
ms.openlocfilehash: 1d05c5d6e25540a5de1b2f8231697c9a738759ce
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216771"
---
# <a name="_div64"></a>_div64

`_div64`內建函式會以32位整數除以64位整數。 傳回值會保存商, 而內建會透過指標參數傳回餘數。 `_div64`是**Microsoft 特有**的。

## <a name="syntax"></a>語法

```C
int _div64(
   __int64 dividend,
   int divisor,
   int* remainder
);
```

### <a name="parameters"></a>參數

*股利* \
在要除數的64位整數。

*divisor* \
在要除以的32位整數。

*數量* \
脫銷餘數的32位整數位。

## <a name="return-value"></a>傳回值

商的32位。

## <a name="remarks"></a>備註

內建函式除以*除數*。 `_div64` 它會將餘數儲存在*餘數*所指向的32位整數中, 並傳回商的32位。

從 Visual Studio 2019 RTM 開始提供內建函式。`_div64`

## <a name="requirements"></a>需求

|內建|架構|標頭|
|---------------|------------------|------------|
|`_div64`|x86、x64|\<immintrin.h>|

## <a name="see-also"></a>另請參閱

[_udiv64](udiv64.md) \
[編譯器內建函式](compiler-intrinsics.md)
