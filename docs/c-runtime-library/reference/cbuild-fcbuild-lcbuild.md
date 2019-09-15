---
title: _Cbuild、_FCbuild、_LCbuild
ms.date: 03/30/2018
api_name:
- _Cbuild
- _FCbuild
- _LCbuild
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
- _Cbuild
- _FCbuild
- _LCbuild
- complex/_Cbuild
- complex/_FCbuild
- complex/_LCbuild
helpviewer_keywords:
- _Cbuild function
- _FCbuild function
- _LCbuild function
ms.openlocfilehash: b0ae50f40f0ca0a926e1eef586c6610a04b6ea7a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70943221"
---
# <a name="_cbuild-_fcbuild-_lcbuild"></a>_Cbuild、_FCbuild、_LCbuild

從實數和虛數部分中，建立複數。

## <a name="syntax"></a>語法

```C
_Dcomplex _Cbuild( double real, double imaginary );
_Fcomplex _FCbuild( float real, float imaginary );
_Lcomplex _LCbuild( long double real, long double imaginary );
```

### <a name="parameters"></a>參數

*real*<br/>
要建立之複數的實數部分。

*imaginary*<br/>
要建立的複數虛數部分。

## <a name="return-value"></a>傳回值

**_Dcomplex**、 **_Fcomplex**或 **_Lcomplex**結構，代表指定之浮點類型值的複數（*real*，*虛* \*數 i）。

## <a name="remarks"></a>備註

**_Cbuild**、 **_FCbuild**和 **_LCbuild**函式簡化複雜類型的建立。 使用[creal、crealf、creall](creal-crealf-creall.md)和[cimag、cimagf、cimagl](cimag-cimagf-cimagl.md)函式來抓取所表示複數的實數和虛數部分。

## <a name="requirements"></a>需求

|常式傳回的值|C 標頭|C++ 標頭|
|-------------|--------------|------------------|
|**_Cbuild**、 **_FCbuild**、 **_LCbuild**|\<complex.h>|\<ccomplex>|

這些是 Microsoft 特有的功能。 **_Dcomplex**、 **_Fcomplex**和 **_Lcomplex**類型分別與未的 C99 原生類型**雙重 _Complex**、 **float _Complex**和**long double _Complex**的對應專案相關。 如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
[_Cmulcc、_FCmulcc、_LCmulcc](cmulcc-fcmulcc-lcmulcc.md)<br/>
[_Cmulcr、_FCmulcr、_LCmulcr](cmulcr-fcmulcr-lcmulcr.md)<br/>
[norm、normf、norml](norm-normf-norml1.md)<br/>
[cproj、cprojf、cprojl](cproj-cprojf-cprojl.md)<br/>
[conj、conjf、conjl](conj-conjf-conjl.md)<br/>
[creal、crealf、creall](creal-crealf-creall.md)<br/>
[cimag、cimagf、cimagl](cimag-cimagf-cimagl.md)<br/>
[carg、cargf、cargl](carg-cargf-cargl.md)<br/>
[cabs、cabsf、cabsl](cabs-cabsf-cabsl.md)<br/>
