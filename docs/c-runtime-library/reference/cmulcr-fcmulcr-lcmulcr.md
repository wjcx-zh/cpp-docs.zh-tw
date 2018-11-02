---
title: _Cmulcr、 _FCmulcr、 _LCmulcr
ms.date: 03/30/2018
apiname:
- _Cmulcr
- _FCmulcr
- _LCmulcr
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
ms.openlocfilehash: ce45b1b1081faba18d8532d3a55d1be877cf84e3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50507480"
---
# <a name="cmulcr-fcmulcr-lcmulcr"></a>_Cmulcr、 _FCmulcr、 _LCmulcr

乘以浮點數的複數。

## <a name="syntax"></a>語法

```C
_Dcomplex _Cmulcr( _Dcomplex x, double y );
_Fcomplex _FCmulcr( _Fcomplex x, float y );
_Lcomplex _LCmulcr( _Lcomplex x, long double y );
```

### <a name="parameters"></a>參數

*x*<br/>
其中一個要相乘的複雜運算元。

*y*<br/>
要相乘的浮點運算元。

## <a name="return-value"></a>傳回值

A **_Dcomplex**， **_Fcomplex**，或 **_Lcomplex**結構，表示複雜的複數乘積*x*和flaoting 點數*y*。

## <a name="remarks"></a>備註

因為 Microsoft 實作的複雜型別上無法運作的內建算術運算子 **_Cmulcr**， **_FCmulcr**，並 **_LCmulcr**函式簡化複雜類型的浮點類型的乘法。

## <a name="requirements"></a>需求

|常式傳回的值|C 標頭|C++ 標頭|
|-------------|--------------|------------------|
|**_Cmulcr**， **_FCmulcr**， **_LCmulcr**|\<complex.h>|\<complex.h>|

這些函式是 Microsoft 特定的。 型別 **_Dcomplex**， **_Fcomplex**，並 **_Lcomplex**是 Microsoft 特定對等項目未實作 C99 原生類型**double _Complex**， **float _Complex**，以及**long double _Complex**分別。 如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

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
