---
title: _Cmulcr、_FCmulcr、_LCmulcr
ms.date: 03/30/2018
api_name:
- _Cmulcr
- _FCmulcr
- _LCmulcr
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
- _Cmulcr
- _FCmulcr
- _LCmulcr
- complex/_Cmulcr
- complex/_FCmulcr
- complex/_LCmulcr
helpviewer_keywords:
- _Cmulcr function
- _FCmulcr function
- _LCmulcr function
ms.openlocfilehash: cbff1c2cb0e66da77b6fdc8127b78fb475aa5080
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942892"
---
# <a name="_cmulcr-_fcmulcr-_lcmulcr"></a>_Cmulcr、_FCmulcr、_LCmulcr

將複數乘以浮點數。

## <a name="syntax"></a>語法

```C
_Dcomplex _Cmulcr( _Dcomplex x, double y );
_Fcomplex _FCmulcr( _Fcomplex x, float y );
_Lcomplex _LCmulcr( _Lcomplex x, long double y );
```

### <a name="parameters"></a>參數

*x*<br/>
要相乘的其中一個複雜運算元。

*y*<br/>
要相乘的浮點運算元。

## <a name="return-value"></a>傳回值

**_Dcomplex**、 **_Fcomplex**或 **_Lcomplex**結構，表示複數*x*和 flaoting-point 數位*y*的複雜乘積。

## <a name="remarks"></a>備註

由於內建算術運算子無法在 Microsoft 的複雜型別上執行，因此 **_Cmulcr**、 **_FCmulcr**和 **_LCmulcr**函式可簡化複雜型別的乘法，方法是使用浮點類型。

## <a name="requirements"></a>需求

|常式傳回的值|C 標頭|C++ 標頭|
|-------------|--------------|------------------|
|**_Cmulcr**、 **_FCmulcr**、 **_LCmulcr**|\<complex.h>|\<complex.h>|

這些是 Microsoft 特有的功能。 **_Dcomplex**、 **_Fcomplex**和 **_Lcomplex**類型分別與未的 C99 原生類型**雙重 _Complex**、 **float _Complex**和**long double _Complex**的對應專案相關。 如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
[_Cbuild、_FCbuild、_LCbuild](cbuild-fcbuild-lcbuild.md)<br/>
[_Cmulcc、_FCmulcc、_LCmulcc](cmulcc-fcmulcc-lcmulcc.md)<br/>
[norm、normf、norml](norm-normf-norml1.md)<br/>
[cproj、cprojf、cprojl](cproj-cprojf-cprojl.md)<br/>
[conj、conjf、conjl](conj-conjf-conjl.md)<br/>
[creal、crealf、creall](creal-crealf-creall.md)<br/>
[cimag、cimagf、cimagl](cimag-cimagf-cimagl.md)<br/>
[carg、cargf、cargl](carg-cargf-cargl.md)<br/>
[cabs、cabsf、cabsl](cabs-cabsf-cabsl.md)<br/>
