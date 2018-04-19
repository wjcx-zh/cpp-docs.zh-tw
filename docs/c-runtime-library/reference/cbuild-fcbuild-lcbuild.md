---
title: _Cbuild _FCbuild，_LCbuild |Microsoft 文件
ms.custom: ''
ms.date: 03/30/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _Cbuild function
- _FCbuild function
- _LCbuild function
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1d5a2a5f40266f490cc0d18614c63715192b0707
ms.sourcegitcommit: 0523c88b24d963c33af0529e6ba85ad2c6ee5afb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2018
---
# <a name="cbuild-fcbuild-lcbuild"></a>_Cbuild _FCbuild _LCbuild

建構從實數和虛數部分的複數。

## <a name="syntax"></a>語法

```C
_Dcomplex _Cbuild( double real, double imaginary );
_Fcomplex _FCbuild( float real, float imaginary );
_Lcomplex _LCbuild( long double real, long double imaginary );
```

### <a name="parameters"></a>參數

*real*<br/>
若要建構中複數的實數部分。

*imaginary*<br/>
若要建構中複數的虛數部分。

## <a name="return-value"></a>傳回值

A **_Dcomplex**， **_Fcomplex**，或**_Lcomplex**結構，表示複數 (*真實*，*虛數* \*我) 指定的浮點類型的值。

## <a name="remarks"></a>備註

**_Cbuild**， **_FCbuild**，和**_LCbuild**函式可簡化建立複雜類型。 使用[creal crealf，creall](../../c-runtime-library/reference/creal-crealf-creall.md)和[cimag cimagf，cimagl](../../c-runtime-library/reference/cimag-cimagf-cimagl.md)函式來擷取表示複數的實數和虛數部分。

## <a name="requirements"></a>需求

|常式|C 標頭|C++ 標頭|
|-------------|--------------|------------------|
|`_Cbuild`,`_FCbuild`, `_LCbuild`|\<complex.h>|\<ccomplex>|

這些函式是 Microsoft 特定的。 型別**_Dcomplex**， **_Fcomplex**，和**_Lcomplex**是 Microsoft 特定對等項目未實作 C99 原生類型**double _Complex**， **float _Complex**，和**長雙精度 _Complex**分別。 如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[_Cmulcc, _FCmulcc, _LCmulcc](../../c-runtime-library/reference/cmulcc-fcmulcc-lcmulcc.md)<br/>
[_Cmulcr, _FCmulcr, _LCmulcr](../../c-runtime-library/reference/cmulcr-fcmulcr-lcmulcr.md)<br/>
[norm、normf、norml](../../c-runtime-library/reference/norm-normf-norml1.md)<br/>
[cproj、cprojf、cprojl](../../c-runtime-library/reference/cproj-cprojf-cprojl.md)<br/>
[conj、conjf、conjl](../../c-runtime-library/reference/conj-conjf-conjl.md)<br/>
[creal、crealf、creall](../../c-runtime-library/reference/creal-crealf-creall.md)<br/>
[cimag、cimagf、cimagl](../../c-runtime-library/reference/cimag-cimagf-cimagl.md)<br/>
[carg、cargf、cargl](../../c-runtime-library/reference/carg-cargf-cargl.md)<br/>
[cabs、cabsf、cabsl](../../c-runtime-library/reference/cabs-cabsf-cabsl.md)<br/>