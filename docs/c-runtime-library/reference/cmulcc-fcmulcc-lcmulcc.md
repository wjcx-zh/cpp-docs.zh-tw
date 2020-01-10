---
title: _Cmulcc、_FCmulcc、_LCmulcc
ms.date: 03/30/2018
api_name:
- _Cmulcc
- _FCmulcc
- _LCmulcc
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
- _Cmulcc
- _FCmulcc
- _LCmulcc
- complex/_Cmulcc
- complex/_FCmulcc
- complex/_LCmulcc
helpviewer_keywords:
- _Cmulcc function
- _FCmulcc function
- _LCmulcc function
ms.openlocfilehash: fc21f8cbd2103993bc2b3e36020c57c8520f04a1
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939067"
---
# <a name="_cmulcc-_fcmulcc-_lcmulcc"></a>_Cmulcc、_FCmulcc、_LCmulcc

將兩個複數相乘。

## <a name="syntax"></a>語法

```C
_Dcomplex _Cmulcc( _Dcomplex x, _Dcomplex y );
_Fcomplex _FCmulcc( _Fcomplex x, _Fcomplex y );
_Lcomplex _LCmulcc( _Lcomplex x, _Lcomplex y );
```

### <a name="parameters"></a>參數

*x*<br/>
要相乘的其中一個複雜運算元。

*y*<br/>
要相乘的另一個複雜運算元。

## <a name="return-value"></a>傳回值

**_Dcomplex**、 **_Fcomplex**或 **_Lcomplex**結構，表示複數*x*和*y*的複雜乘積。

## <a name="remarks"></a>備註

由於內建算術運算子無法在 Microsoft 的複雜型別上執行，因此 **_Cmulcc**、 **_FCmulcc**和 **_LCmulcc**函數可簡化複雜型別的乘法。

## <a name="requirements"></a>需求

|常式傳回的值|C 標頭|C++ 標頭|
|-------------|--------------|------------------|
|**_Cmulcc**、 **_FCmulcc**、 **_LCmulcc**|\<complex.h>|\<complex.h>|

這些是 Microsoft 特有的功能。 **_Dcomplex**、 **_Fcomplex**和 **_Lcomplex**類型分別與未的 C99 原生類型**雙重 _Complex**、 **float _Complex**和**long double _Complex**的對應專案相關。 如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
[_Cbuild、_FCbuild、_LCbuild](cbuild-fcbuild-lcbuild.md)<br/>
[_Cmulcr、_FCmulcr、_LCmulcr](cmulcr-fcmulcr-lcmulcr.md)<br/>
[norm、normf、norml](norm-normf-norml1.md)<br/>
[cproj、cprojf、cprojl](cproj-cprojf-cprojl.md)<br/>
[conj、conjf、conjl](conj-conjf-conjl.md)<br/>
[creal、crealf、creall](creal-crealf-creall.md)<br/>
[cimag、cimagf、cimagl](cimag-cimagf-cimagl.md)<br/>
[carg、cargf、cargl](carg-cargf-cargl.md)<br/>
[cabs、cabsf、cabsl](cabs-cabsf-cabsl.md)<br/>
