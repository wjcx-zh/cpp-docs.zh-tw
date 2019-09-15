---
title: nearbyint、nearbyintf、nearbyintl
ms.date: 04/05/2018
api_name:
- nearbyint
- nearbyintf
- nearbyintl
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
- nearbyint
- nearbyintf
- nearbyintl
- math/nearbyint
- math/narbyintf
- math/narbyintl
helpviewer_keywords:
- nearbyint function
- nearbyintf function
- nearbyintl function
ms.assetid: dd39cb68-96b0-434b-820f-6ff2ea65584f
ms.openlocfilehash: cd0a7d00c5019dd1e483d555df6db8d9770e61c1
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951398"
---
# <a name="nearbyint-nearbyintf-nearbyintl"></a>nearbyint、nearbyintf、nearbyintl

將指定的浮點值四捨五入成整數，並以浮點數格式傳回該值。

## <a name="syntax"></a>語法

```C
double nearbyint( double x );
float nearbyintf( float x );
long double nearbyintl( long double x );
```

```cpp
float nearbyint( float x ); //C++ only
long double nearbyint( long double x ); //C++ only
```

### <a name="parameters"></a>參數

*x*<br/>
要捨入的值。

## <a name="return-value"></a>傳回值

如果成功，會使用[fegetround](fegetround-fesetround2.md)所報告的目前舍入格式，將*x*四捨五入成最接近的整數。 否則，此函式可能會傳回下列其中一個值：

|問題|Return|
|-----------|------------|
|*x* = ±INFINITY|±無限大，未修改|
|*x* = ±0|±0，未修改|
|*x* = NaN|NaN|

錯誤不會透過[_matherr](matherr.md)報告;具體而言，此函數不會報告任何**FE_INEXACT**例外狀況。

## <a name="remarks"></a>備註

此函式與[rint](rint-rintf-rintl.md)之間的主要差異在於，此函式不會引發不精確的浮點例外狀況。

因為最大浮點值是精確的整數，所以此函式自身永遠不會溢位；相反地，根據您使用的函式版本，輸出可能會造成傳回值溢位。

C++允許多載，因此您可以呼叫採用並傳回**float**或**long** **double**參數的**nearbyint**多載。 在 C 程式中， **nearbyint**一律會採用兩個雙精度浮點數，並傳回雙精度值。

## <a name="requirements"></a>需求

|函數|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**nearbyint**、 **nearbyintf**、 **nearbyintl**|\<math.h>|\<cmath> 或 \<math.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
[數學和浮點支援](../floating-point-support.md)<br/>
