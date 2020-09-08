---
title: ctan、ctanf、ctanl
description: Ctan、ctanf 和 ctanl 的 API 參考;它會取出複數的正切函數。
ms.date: 11/04/2016
api_name:
- ctan
- ctanf
- ctanl
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
- ctan
- ctanf
- ctanl
- complex/ctan
- complex/ctanf
- complex/ctanl
helpviewer_keywords:
- ctan function
- ctanf function
- ctanl function
ms.assetid: d3cbd25c-1e93-4a6d-8154-da42921f7223
ms.openlocfilehash: 74fa33a6bf6b99e8606094aff3845fdfd79d48a2
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555900"
---
# <a name="ctan-ctanf-ctanl"></a>ctan、ctanf、ctanl

擷取複數的正切值。

## <a name="syntax"></a>語法

```C
_Dcomplex ctan(
   _Dcomplex z
);
_Fcomplex ctan(
   _Fcomplex z
);  // C++ only
_Lcomplex ctan(
   _Lcomplex z
);  // C++ only
_Fcomplex ctanf(
   _Fcomplex z
);
_Lcomplex ctanl(
   _Lcomplex z
);
```

### <a name="parameters"></a>參數

*Z*\
代表角度的複數 (弧度)。

## <a name="return-value"></a>傳回值

*Z*的正切函數。

|輸入|SEH 例外狀況|**_matherr** 例外|
|-----------|-------------------|--------------------------|
|±∞、QNAN、IND|無|_DOMAIN|
|±∞ (**tan**， **tanf**) |無效|_DOMAIN|

## <a name="remarks"></a>備註

因為 c + + 允許多載，所以您可以呼叫採用並傳回 **_Fcomplex**和 **_Lcomplex**值的**ctan**多載。 在 C 程式中， **ctan** 一律會採用並傳回 **_Dcomplex** 值。

## <a name="requirements"></a>規格需求

|常式傳回的值|C 標頭|C++ 標頭|
|-------------|--------------|------------------|
|**ctan**、  **ctanf**、 **ctanl**|\<complex.h>|\<ccomplex>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函數參考](crt-alphabetical-function-reference.md)<br/>
[catanh、catanhf、catanhl](catanh-catanhf-catanhl.md)<br/>
[ctanh、ctanhf、ctanhl](ctanh-ctanhf-ctanhl.md)<br/>
[catan、catanf、catanl](catan-catanf-catanl.md)<br/>
[csinh、csinhf、csinhl](csinh-csinhf-csinhl.md)<br/>
[casinh、casinhf、casinhl](casinh-casinhf-casinhl.md)<br/>
[ccosh、ccoshf、ccoshl](ccosh-ccoshf-ccoshl.md)<br/>
[cacosh、cacoshf、cacoshl](cacosh-cacoshf-cacoshl.md)<br/>
[cacos、cacosf、cacosl](cacos-cacosf-cacosl.md)<br/>
[csin、csinf、csinl](csin-csinf-csinl.md)<br/>
[casin、casinf、casinl](casin-casinf-casinl.md)<br/>
[ccos、ccosf、ccosl](ccos-ccosf-ccosl.md)<br/>
[csqrt、csqrtf、csqrtl](csqrt-csqrtf-csqrtl.md)<br/>
