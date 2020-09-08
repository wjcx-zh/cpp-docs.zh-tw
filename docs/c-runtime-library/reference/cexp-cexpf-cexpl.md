---
title: cexp、cexpf、cexpl
description: Cexp、cexpf 和 cexpl 的 API 參考;這會計算複數的底數-e 指數。
ms.date: 11/04/2016
api_name:
- cexp
- cexpf
- cexpl
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
- cexp
- cexpf
- cexpl
- complex/cepx
- complex/cexpf
- complex/cexpl
helpviewer_keywords:
- cexp function
- cexpl function
- cexpf function
ms.assetid: f27fd5a9-70c7-4957-a7ee-5256d19bd1da
ms.openlocfilehash: 66f7b687e8da12473abef4dbc44831e175956ac0
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555211"
---
# <a name="cexp-cexpf-cexpl"></a>cexp、cexpf、cexpl

計算底數為 e 之複數的指數。

## <a name="syntax"></a>語法

```C
_Dcomplex cexp( _Dcomplex z );
_Fcomplex cexpf( _Fcomplex z );
_Lcomplex cexpl( _Lcomplex z );

_Fcomplex cexp( _Fcomplex z );  // C++ only
_Lcomplex cexp( _Lcomplex z );  // C++ only
```

### <a name="parameters"></a>參數

*Z*\
代表指數的複數。

## <a name="return-value"></a>傳回值

**E**的值會提升為*z*的乘冪。

## <a name="remarks"></a>備註

因為 c + + 允許多載，所以您可以呼叫採用並傳回 **_Fcomplex**和 **_Lcomplex**值的**cexp**多載。 在 C 程式中， **cexp** 一律會採用並傳回 **_Dcomplex** 值。

## <a name="requirements"></a>規格需求

|常式傳回的值|C 標頭|C++ 標頭|
|-------------|--------------|------------------|
|**cexp**、 **cexpf**、 **cexpl**|\<complex.h>|\<complex.h>|

如需相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函數參考](crt-alphabetical-function-reference.md)\
[cpow、cpowf、cpowl](cpow-cpowf-cpowl.md)\
[clog10、clog10f、clog10l](clog10-clog10f-clog10l.md)\
[clog、clogf、clogl](clog-clogf-clogl.md)
