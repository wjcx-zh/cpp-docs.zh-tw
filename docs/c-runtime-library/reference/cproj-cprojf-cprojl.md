---
title: cproj、cprojf、cprojl
description: Cproj、cprojf 和 cprojl 的 API 參考;它會在黎曼球面球體上取出複數的投射。
ms.date: 9/2/2020
api_name:
- cproj
- cprojf
- cprojl
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
- cproj
- cprojf
- cprojl
- complex/cproj
- complex/cprojf
- complex/cprojl
helpviewer_keywords:
- cproj function
- cprojf function
- cprojl function
ms.assetid: 32b49623-13bf-4cae-802e-7912d75030fe
ms.openlocfilehash: fcc3c0a42c8c6392130ad58ed12c4985e7ad4907
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555939"
---
# <a name="cproj-cprojf-cprojl"></a>cproj、cprojf、cprojl

擷取黎曼球面上複數的投影。

## <a name="syntax"></a>語法

```C
_Dcomplex cproj(
   _Dcomplex z
);
_Fcomplex cproj(
   _Fcomplex z
);  // C++ only
_Lcomplex cproj(
   _Lcomplex z
);  // C++ only
_Fcomplex cprojf(
   _Fcomplex z
);
_Lcomplex cprojl(
   _Lcomplex z
);
#define cproj(X) // Requires C11 or higher
```

### <a name="parameters"></a>參數

*Z*\
複數。

## <a name="return-value"></a>傳回值

黎曼球面球體上 *z* 的投射。

## <a name="remarks"></a>備註

因為 c + + 允許多載，所以您可以呼叫採用並傳回 **_Fcomplex**和 **_Lcomplex**值的**cproj**多載。 在 C 程式中，除非您要使用 \<tgmath.h> 宏來呼叫這個函式，否則 **cproj** 一律會採用並傳回 **_Dcomplex** 值。

如果您使用 \<tgmath.h> `cproj()` 宏，則引數的類型會決定所選取的函式版本。 如需詳細資料，請參閱 [類型-泛型數學](../../c-runtime-library/tgmath.md) 。

## <a name="requirements"></a>規格需求

|常式傳回的值|C 標頭|C++ 標頭|
|-------------|--------------|------------------|
|**cproj**、 **cprojf**、 **cprojl**|\<complex.h>|\<ccomplex>|
|**cproj** 宏 | \<tgmath.h> ||

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函數參考](crt-alphabetical-function-reference.md)<br/>
[norm、normf、norml](norm-normf-norml1.md)<br/>
[creal、crealf、creall](creal-crealf-creall.md)<br/>
[conj、conjf、conjl](conj-conjf-conjl.md)<br/>
[cimag、cimagf、cimagl](cimag-cimagf-cimagl.md)<br/>
[carg、cargf、cargl](carg-cargf-cargl.md)<br/>
[cabs、cabsf、cabsl](cabs-cabsf-cabsl.md)<br/>
