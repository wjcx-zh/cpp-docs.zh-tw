---
title: cosh、 coshf、 coshl
ms.date: 04/11/2018
apiname:
- cosh
- coshf
- coshl
apilocation:
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
apitype: DLLExport
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
ms.openlocfilehash: 0f55e084e760cb6d04dbe7ec4fefb5e2ac1d79fd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50609530"
---
# <a name="cosh-coshf-coshl"></a>cosh、 coshf、 coshl

計算雙曲餘弦值。

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

雙曲線餘弦*x*。

根據預設，如果結果太大而無法在**cosh**， **coshf**，或**coshl**呼叫，則函數會傳回**HUGE_VAL**並設定**errno**要**ERANGE**。

|輸入|SEH 例外狀況|Matherr 例外狀況|
|-----------|-------------------|-----------------------|
|常见**QNAN**， **IND**|無|**（_D)**|
|*x* ≥ 7.104760e+002|**精確**+**溢位**|**溢位**|

## <a name="remarks"></a>備註

因為 c + + 允許多載，您可以呼叫多載**cosh**採用並傳回**float**或是**長** **double**值。 在 C 程式中， **cosh**一律採用並傳回**double**。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭 (C)|必要的標頭 (C++)|
|-------------|---------------------|-|
|**coshf**， **cosl**， **coshl**|\<math.h>|\<cmath> 或 \<math.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱中的範例[sinh、 sinhf、 sinhl](sinh-sinhf-sinhl.md)。

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[acosh、acoshf、acoshl](acosh-acoshf-acoshl.md)<br/>
[asinh、asinhf、asinhl](asinh-asinhf-asinhl.md)<br/>
[atanh、atanhf、atanhl](atanh-atanhf-atanhl.md)<br/>
[_matherr](matherr.md)<br/>
[sinh、sinhf、sinhl](sinh-sinhf-sinhl.md)<br/>
[tanh、tanhf、tanhl](tanh-tanhf-tanhl.md)<br/>
