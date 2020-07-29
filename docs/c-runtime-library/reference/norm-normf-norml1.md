---
title: norm、normf、norml
ms.date: 04/05/2018
api_name:
- norm
- normf
- norml
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
ms.openlocfilehash: 38e7283ca5acd5571589d3ef0b19c626806e4bca
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234051"
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

*Z*的平方大小。

## <a name="remarks"></a>備註

因為 c + + 允許多載，所以您可以呼叫採用 **_Fcomplex**或 **_Lcomplex**值，並傳回或值的**標準**多載 **`float`** **`long double`** 。 在 C 程式中，「**標準**」一律採用 **_Dcomplex**值，並傳回 **`double`** 值。

## <a name="requirements"></a>需求

|常式傳回的值|C 標頭|C++ 標頭|
|-------------|--------------|------------------|
|**標準**、 **normf**、 **norml**|\<complex.h>|\<complex.h>|

**_Fcomplex**、 **_Dcomplex**和 **_Lcomplex**類型分別是 Microsoft 特定的對等專案，而不是原生 C99 類型的**浮點數 _Complex**、 **double _Complex**和**long double _Complex**。  如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函數參考](crt-alphabetical-function-reference.md)<br/>
[creal、crealf、creall](creal-crealf-creall.md)<br/>
[cproj、cprojf、cprojl](cproj-cprojf-cprojl.md)<br/>
[conj、conjf、conjl](conj-conjf-conjl.md)<br/>
[cimag、cimagf、cimagl](cimag-cimagf-cimagl.md)<br/>
[carg、cargf、cargl](carg-cargf-cargl.md)<br/>
[cabs、cabsf、cabsl](cabs-cabsf-cabsl.md)<br/>
