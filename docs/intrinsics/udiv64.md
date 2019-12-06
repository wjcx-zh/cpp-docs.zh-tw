---
title: _udiv64
ms.date: 09/02/2019
f1_keywords:
- _udiv64
helpviewer_keywords:
- _udiv64 intrinsic
ms.openlocfilehash: ddb46f33b0fccc1cedc2a704265b096ba715b506
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857992"
---
# <a name="_udiv64"></a>_udiv64

`_udiv64` 內建會以32位不帶正負號的整數除以64位不帶正負號的整數。 傳回值會保存商，而內建會透過指標參數傳回餘數。 `_udiv64` 是**Microsoft 特有**的。

## <a name="syntax"></a>語法

```C
unsigned int _udiv64(
   unsigned __int64 dividend,
   unsigned int divisor,
   unsigned int* remainder
);
```

### <a name="parameters"></a>參數

被*除數*\
在要除數的64位不帶正負號的整數。

*除數*\
在要除以的32位不帶正負號整數。

*餘數*\
脫銷32位不帶正負號的整數餘數。

## <a name="return-value"></a>傳回值

商的32位。

## <a name="remarks"></a>備註

`_udiv64` 內建除以*除數*的*除數*。 它會將餘數儲存在*餘數*所指向的32位不帶正負號整數中，並傳回商的32位。

從 Visual Studio 2019 RTM 開始提供 `_udiv64` 內建。

## <a name="requirements"></a>需求

|內建|架構|標頭|
|---------------|------------------|------------|
|`_udiv64`|x86、x64|\<immintrin.h>. h >|

## <a name="see-also"></a>請參閱

[_div64](div64.md) \
[編譯器內建函式](compiler-intrinsics.md)
