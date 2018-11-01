---
title: _Cbuild、 _FCbuild、 _LCbuild
ms.date: 03/30/2018
apiname:
- _Cbuild
- _FCbuild
- _LCbuild
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
ms.openlocfilehash: 5565c87a3cccd1715a1357f417238587f3fba4d5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50511796"
---
# <a name="cbuild-fcbuild-lcbuild"></a>_Cbuild、 _FCbuild、 _LCbuild

建構複數的實數和虛數部分。

## <a name="syntax"></a>語法

```C
_Dcomplex _Cbuild( double real, double imaginary );
_Fcomplex _FCbuild( float real, float imaginary );
_Lcomplex _LCbuild( long double real, long double imaginary );
```

### <a name="parameters"></a>參數

*real*<br/>
建構中複數的實數部分。

*虛數*<br/>
建構中複數的虛數部分。

## <a name="return-value"></a>傳回值

A **_Dcomplex**， **_Fcomplex**，或 **_Lcomplex**結構，表示複數 (*實際*，*虛數* \*我) 指定的浮點類型的值。

## <a name="remarks"></a>備註

**_Cbuild**， **_FCbuild**，並 **_LCbuild**函式簡化建立複雜型別。 使用[creal、 crealf、 creall](creal-crealf-creall.md)並[cimag、 cimagf、 cimagl](cimag-cimagf-cimagl.md)函式來擷取表示複數的實數和虛數部分。

## <a name="requirements"></a>需求

|常式傳回的值|C 標頭|C++ 標頭|
|-------------|--------------|------------------|
|**_Cbuild**， **_FCbuild**， **_LCbuild**|\<complex.h>|\<ccomplex>|

這些函式是 Microsoft 特定的。 型別 **_Dcomplex**， **_Fcomplex**，並 **_Lcomplex**是 Microsoft 特定對等項目未實作 C99 原生類型**double _Complex**， **float _Complex**，以及**long double _Complex**分別。 如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

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
