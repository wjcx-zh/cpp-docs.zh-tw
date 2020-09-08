---
title: conj、conjf、conjl
description: Conj、conjf 和 conjl 的 API 參考;它會抓取複數的共軛複數。
ms.date: 9/2/2020
api_name:
- conj
- conjf
- conjl
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
- conj
- conjf
- conjl
- complex/conj
- complex/conjf
- complex/conjl
helpviewer_keywords:
- conj function
- conjf function
- conjl function
ms.assetid: 792fccfa-19c6-4890-99f9-a3b89effccd6
ms.openlocfilehash: b779eb2d92893b204a73b2fa4f5c89928933ffeb
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556349"
---
# <a name="conj-conjf-conjl"></a>conj、conjf、conjl

擷取複數的共軛複數。

## <a name="syntax"></a>語法

```C
_Dcomplex conj(
   _Dcomplex z
);
_Fcomplex conj(
   _Fcomplex z
);  // C++ only
_Lcomplex conj(
   _Lcomplex z
);  // C++ only
_Fcomplex conjf(
   _Fcomplex z
);
_Lcomplex conjl(
   _Lcomplex z
);
#define conj(X) // Requires C11 or higher
```

### <a name="parameters"></a>參數

*Z*\
複數。

## <a name="return-value"></a>傳回值

*Z*的共軛複數。  結果與 *z*具有相同的實數和虛數部分，但是正負號相反。

## <a name="remarks"></a>備註

因為 c + + 允許多載，所以您可以呼叫採用並傳回 **_Fcomplex**和 **_Lcomplex**值的**conj**多載。 在 C 程式中，除非您要使用 \<tgmath.h> 宏來呼叫這個函式，否則 **conj** 一律會採用並傳回 **_Dcomplex** 值。

如果您使用 \<tgmath.h> `conj()` 宏，則引數的類型會決定所選取的函式版本。 如需詳細資料，請參閱 [類型-泛型數學](../../c-runtime-library/tgmath.md) 。

## <a name="requirements"></a>規格需求

|常式傳回的值|C 標頭|C++ 標頭|
|-------------|--------------|------------------|
|**conj**、 **conjf**、 **conjl**|\<complex.h>|\<ccomplex>|
|**conj** 宏 | \<tgmath.h> ||

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函數參考](crt-alphabetical-function-reference.md)<br/>
[norm、normf、norml](norm-normf-norml1.md)<br/>
[creal、crealf、creall](creal-crealf-creall.md)<br/>
[cproj、cprojf、cprojl](cproj-cprojf-cprojl.md)<br/>
[cimag、cimagf、cimagl](cimag-cimagf-cimagl.md)<br/>
[carg、cargf、cargl](carg-cargf-cargl.md)<br/>
[cabs、cabsf、cabsl](cabs-cabsf-cabsl.md)<br/>
