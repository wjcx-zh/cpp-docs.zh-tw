---
title: creal、crealf、creall | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- creal
- crealf
- creall
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
- creal
- crealf
- creall
- complex/creal
- complex/crealf
- complex/creall
dev_langs:
- C++
helpviewer_keywords:
- creal function
- crealf function
- creall function
ms.assetid: fa3ac62f-7aa3-4238-a71f-d6b00cd0c7c8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6b8d3ca02aeb0f3f9b12c8b82cbb27d9bd3ad3aa
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="creal-crealf-creall"></a>creal、crealf、creall

擷取複數的實數部分。

## <a name="syntax"></a>語法

```C
double creal( _Dcomplex z );
float crealf( _Fcomplex z );
long double creall( _Lcomplex z );
```

```cpp
float creal( _Fcomplex z );  // C++ only
long double creal( _Lcomplex z );  // C++ only
```

### <a name="parameters"></a>參數

*z*<br/>
複數。

## <a name="return-value"></a>傳回值

實數部分*z*。

## <a name="remarks"></a>備註

因為 c + + 允許多載，所以您可以呼叫的多載**creal**採用 **_Fcomplex**或 **_Lcomplex**值，並傳回**float**或**長雙精度**值。 在 C 程式中， **creal**一律採用 **_Dcomplex**值並傳回**double**值。

## <a name="requirements"></a>需求

|常式|C 標頭|C++ 標頭|
|-------------|--------------|------------------|
|**creal**， **crealf**， **creall**|\<complex.h>|\<ccomplex>|

**_Fcomplex**， **_Dcomplex**，和 **_Lcomplex**型別是 Microsoft 特定的對等的未實作的原生 C99 類型**float _Complex**， **double _Complex**，和**長雙精度 _Complex**分別。 如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
[_Cbuild、_FCbuild、_LCbuild](cbuild-fcbuild-lcbuild.md)<br/>
[norm、normf、norml](norm-normf-norml1.md)<br/>
[cproj、cprojf、cprojl](cproj-cprojf-cprojl.md)<br/>
[conj、conjf、conjl](conj-conjf-conjl.md)<br/>
[cimag、cimagf、cimagl](cimag-cimagf-cimagl.md)<br/>
[carg、cargf、cargl](carg-cargf-cargl.md)<br/>
[cabs、cabsf、cabsl](cabs-cabsf-cabsl.md)<br/>