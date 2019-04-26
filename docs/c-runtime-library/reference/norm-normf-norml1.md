---
title: norm、normf、norml
ms.date: 04/05/2018
apiname:
- norm
- normf
- norml
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
- norm
- normf
- norml
- complex/norm
- complex/normf
- complex/norml
helpviewer_keywords:
- norm function
- normf function
- norml function
ms.assetid: 9786ecfe-0019-4553-b378-0af6c691e15c
ms.openlocfilehash: 3c1803a54f0dfc27975af5bb0eeb7e5c042b2579
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156132"
---
# <a name="norm-normf-norml"></a>norm、normf、norml

擷取複數的平方大小。

## <a name="syntax"></a>語法

```C
double norm( _Dcomplex z );
float normf( _Fcomplex z );
long double norml( _Lcomplex z );
```

```cpp
float norm( _Fcomplex z );  // C++ only
long double norm( _Lcomplex z );  // C++ only
```

### <a name="parameters"></a>參數

*z*<br/>
複數。

## <a name="return-value"></a>傳回值

平方的大小*z*。

## <a name="remarks"></a>備註

因為C++允許多載，您可以呼叫多載**norm**採用 **_Fcomplex**或 **_Lcomplex**的值，並傳回**float**或是**長雙精度**值。 在 C 程式中， **norm**一律採用 **_Dcomplex**值，然後傳回**double**值。

## <a name="requirements"></a>需求

|常式傳回的值|C 標頭|C++ 標頭|
|-------------|--------------|------------------|
|**norm**， **normf**， **norml**|\<complex.h>|\<complex.h>|

**_Fcomplex**， **_Dcomplex**，並 **_Lcomplex**型別是 Microsoft 特定對等項目未實作的原生 C99 類型**float _Complex**， **double _Complex**，以及**long double _Complex**分別。  如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
[creal、crealf、creall](creal-crealf-creall.md)<br/>
[cproj、cprojf、cprojl](cproj-cprojf-cprojl.md)<br/>
[conj、conjf、conjl](conj-conjf-conjl.md)<br/>
[cimag、cimagf、cimagl](cimag-cimagf-cimagl.md)<br/>
[carg、cargf、cargl](carg-cargf-cargl.md)<br/>
[cabs、cabsf、cabsl](cabs-cabsf-cabsl.md)<br/>
