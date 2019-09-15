---
title: cosh、coshf、coshl
ms.date: 04/11/2018
api_name:
- cosh
- coshf
- coshl
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
- cosh
- coshf
- coshl
helpviewer_keywords:
- cosh function
- coshf function
- coshl function
- trigonometric functions
- hyperbolic functions
ms.openlocfilehash: 446988e67ca6e3b4a3839a9336f1ea4e2755c124
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938988"
---
# <a name="cosh-coshf-coshl"></a>cosh、coshf、coshl

計算雙曲余弦值。

## <a name="syntax"></a>語法

```C
double cosh( double x );
float coshf( float x );
long double coshl( long double x );
```

```cpp
float cosh( float x );  // C++ only
long double cosh( long double x );  // C++ only
```

### <a name="parameters"></a>參數

*x*<br/>
角度 (弧度)。

## <a name="return-value"></a>傳回值

*X*的雙曲余弦值。

根據預設，如果**cosh**、 **coshf**或**coshl**呼叫中的結果太大，函式會傳回**HUGE_VAL** ，並將**errno**設定為**ERANGE**。

|Input|SEH 例外狀況|Matherr 例外狀況|
|-----------|-------------------|-----------------------|
|± **QNAN**， **IND**|none|**_DOMAIN**|
|*x* ≥ 7.104760e+002|**INEXACT**+**OVERFLOW**|**OVERFLOW**|

## <a name="remarks"></a>備註

因為C++允許多載，所以您可以呼叫採用並傳回**float**或**long** **double**值之**cosh**的多載。 在 C 程式中， **cosh**一律會採用並傳回**雙精度浮點數**。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭 (C)|必要的標頭 (C++)|
|-------------|---------------------|-|
|**coshf**、 **cosl**、 **coshl**|\<math.h>|\<cmath> 或 \<math.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱[sinh、sinhf、sinhl](sinh-sinhf-sinhl.md)中的範例。

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[acosh、acoshf、acoshl](acosh-acoshf-acoshl.md)<br/>
[asinh、asinhf、asinhl](asinh-asinhf-asinhl.md)<br/>
[atanh、atanhf、atanhl](atanh-atanhf-atanhl.md)<br/>
[_matherr](matherr.md)<br/>
[sinh、sinhf、sinhl](sinh-sinhf-sinhl.md)<br/>
[tanh、tanhf、tanhl](tanh-tanhf-tanhl.md)<br/>
