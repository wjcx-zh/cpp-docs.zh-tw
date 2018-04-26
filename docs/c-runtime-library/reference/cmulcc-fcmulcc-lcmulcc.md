---
title: _Cmulcc _FCmulcc，_LCmulcc |Microsoft 文件
ms.custom: ''
ms.date: 03/30/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- _Cmulcc
- _FCmulcc
- _LCmulcc
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
- _Cmulcc
- _FCmulcc
- _LCmulcc
- complex/_Cmulcc
- complex/_FCmulcc
- complex/_LCmulcc
dev_langs:
- C++
helpviewer_keywords:
- _Cmulcc function
- _FCmulcc function
- _LCmulcc function
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 282dfcc7529ec0be779bee6660a94bfd3dd502bc
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="cmulcc-fcmulcc-lcmulcc"></a>_Cmulcc _FCmulcc _LCmulcc

乘上兩個複數。

## <a name="syntax"></a>語法

```C
_Dcomplex _Cmulcc( _Dcomplex x, _Dcomplex y );
_Fcomplex _FCmulcc( _Fcomplex x, _Fcomplex y );
_Lcomplex _LCmulcc( _Lcomplex x, _Lcomplex y );
```

### <a name="parameters"></a>參數

*x*<br/>
要相乘的複雜運算元的其中一個。

*y*<br/>
其他複雜運算元相乘。

## <a name="return-value"></a>傳回值

A **_Dcomplex**， **_Fcomplex**，或 **_Lcomplex**結構，表示複雜複雜的數字的乘積*x*和*y*。

## <a name="remarks"></a>備註

因為內建算術運算子無法運作的複雜型別中，Microsoft 實作 **_Cmulcc**， **_FCmulcc**，和 **_LCmulcc**函式簡化複雜型別的乘法。

## <a name="requirements"></a>需求

|常式|C 標頭|C++ 標頭|
|-------------|--------------|------------------|
|**_Cmulcc**， **_FCmulcc**， **_LCmulcc**|\<complex.h>|\<complex.h>|

這些函式是 Microsoft 特定的。 型別 **_Dcomplex**， **_Fcomplex**，和 **_Lcomplex**是 Microsoft 特定對等項目未實作 C99 原生類型**double _Complex**， **float _Complex**，和**長雙精度 _Complex**分別。 如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

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
