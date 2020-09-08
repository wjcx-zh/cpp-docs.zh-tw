---
title: creal、crealf、creall
description: Creal、crealf、creall 的 API 參考;它會取出複數的實數部分。
ms.date: 9/2/2020
api_name:
- creal
- crealf
- creall
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
- creal
- crealf
- creall
- complex/creal
- complex/crealf
- complex/creall
helpviewer_keywords:
- creal function
- crealf function
- creall function
ms.assetid: fa3ac62f-7aa3-4238-a71f-d6b00cd0c7c8
ms.openlocfilehash: 4f375bbe8813ba67130f8b56d8e2c99d5b734764
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555926"
---
# <a name="creal-crealf-creall"></a>creal、crealf、creall

擷取複數的實數部分。

## <a name="syntax"></a>語法

```C
double creal( _Dcomplex z );
float crealf( _Fcomplex z );
long double creall( _Lcomplex z );
#define creal(X) // Requires C11 or higher

float creal( _Fcomplex z );  // C++ only
long double creal( _Lcomplex z );  // C++ only
```

### <a name="parameters"></a>參數

*Z*<br/>
複數。

## <a name="return-value"></a>傳回值

*Z*的實數部分。

## <a name="remarks"></a>備註

因為 c + + 允許多載，所以您可以呼叫採用 **_Fcomplex**或 **_Lcomplex**值和傳回值的**creal**多載 **`float`** **`long double`** 。 在 C 程式中，除非您使用 \<tgmath.h> 宏來呼叫這個函式，否則 **creal** 一律會採用 **_Dcomplex** 值並傳回 **`double`** 值。

如果您使用 \<tgmath.h> `creal()` 宏，則引數的類型會決定所選取的函式版本。 如需詳細資料，請參閱 [類型-泛型數學](../../c-runtime-library/tgmath.md) 。

## <a name="requirements"></a>規格需求

|常式傳回的值|C 標頭|C++ 標頭|
|-------------|--------------|------------------|
|**creal**、 **crealf**、 **creall**|\<complex.h>|\<ccomplex>|
|**creal** 宏 | \<tgmath.h> ||

**_Fcomplex**、 **_Dcomplex**和 **_Lcomplex**型別分別是 Microsoft 特定的原生 C99**型別 float _Complex**、 **double _Complex**和**long double _Complex**。 如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函數參考](crt-alphabetical-function-reference.md)<br/>
[_Cbuild、_FCbuild、_LCbuild](cbuild-fcbuild-lcbuild.md)<br/>
[norm、normf、norml](norm-normf-norml1.md)<br/>
[cproj、cprojf、cprojl](cproj-cprojf-cprojl.md)<br/>
[conj、conjf、conjl](conj-conjf-conjl.md)<br/>
[cimag、cimagf、cimagl](cimag-cimagf-cimagl.md)<br/>
[carg、cargf、cargl](carg-cargf-cargl.md)<br/>
[cabs、cabsf、cabsl](cabs-cabsf-cabsl.md)<br/>
