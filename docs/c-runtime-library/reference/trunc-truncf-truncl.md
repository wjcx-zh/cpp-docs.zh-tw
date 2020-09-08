---
title: trunc、truncf、truncl
description: Trunc、truncf、truncl 的 API 參考;，決定最接近或等於指定之浮點值的最接近整數。
ms.date: 9/1/2020
api_name:
- trunc
- truncf
- truncl
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-math-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- trunc
- truncf
- truncl
- math/trunc
- math/truncf
- math/truncl
helpviewer_keywords:
- trunc function
- truncf function
- truncl function
ms.assetid: de2038ac-ac0b-483e-870c-e8992dcd4fd0
ms.openlocfilehash: f1f2fde95bb944aa461bb95a9ad30fac204552b9
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556628"
---
# <a name="trunc-truncf-truncl"></a>trunc、truncf、truncl

判斷小於或等於指定浮點值且最接近的整數。

## <a name="syntax"></a>語法

```C
double trunc( double x );
long double truncl( long double x );
#define trunc(X) // Requires C11 or higher

long double trunc( long double x ); //C++ only
float trunc( float x ); //C++ only
```

### <a name="parameters"></a>參數

*X*\
要截斷的值。

## <a name="return-value"></a>傳回值

如果成功，則傳回 *x*的整數值，舍入為零。

否則，可能會傳回下列其中一項：

|問題|傳回|
|-----------|------------|
|*x* = ±無限大|x|
|*x* = ±0|x|
|*x* = NaN|NaN|

依 [_matherr](matherr.md) 中的指定回報錯誤。

## <a name="remarks"></a>備註

因為 c + + 允許多載，所以您可以呼叫採用和傳回和類型的 **trunc** 多載 **`float`** **`long double`** 。 在 C 程式中，除非您要使用 \<tgmath.h> 宏來呼叫這個函式，否則 **trunc** 一律會採用並傳回 **`double`** 。

如果您使用 \<tgmath.h> `trunc()` 宏，則引數的類型會決定所選取的函式版本。 如需詳細資料，請參閱 [類型-泛型數學](../../c-runtime-library/tgmath.md) 。

因為浮點數的最大值是確切的整數，這個函式本身不會溢位。 不過，您可能會因為將值傳回到整數類型而造成函式溢位。

您也可以透過隱含地從浮點數轉換為整數進行無條件捨去。不過，這麼做受限於可以用目標類型儲存的值。

## <a name="requirements"></a>規格需求

|函式|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**trunc**、 **truncf**、 **truncl**|\<math.h>|\<cmath>|
|**trunc** 宏 | \<tgmath.h> ||

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函數參考](crt-alphabetical-function-reference.md)<br/>
[floor、floorf、floorl](floor-floorf-floorl.md)<br/>
[ceil、ceilf、ceill](ceil-ceilf-ceill.md)<br/>
[round、roundf、roundl](round-roundf-roundl.md)<br/>
