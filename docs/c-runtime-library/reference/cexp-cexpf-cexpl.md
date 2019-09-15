---
title: cexp、cexpf、cexpl
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
ms.openlocfilehash: 0dd6c9deddfe93cf044985f93b2129695d0770f0
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70943161"
---
# <a name="cexp-cexpf-cexpl"></a>cexp、cexpf、cexpl

計算底數為 e 之複數的指數。

## <a name="syntax"></a>語法

```C
_Dcomplex cexp( _Dcomplex z );
_Fcomplex cexpf( _Fcomplex z );
_Lcomplex cexpl( _Lcomplex z );
```

```cpp
_Fcomplex cexp( _Fcomplex z );  // C++ only
_Lcomplex cexp( _Lcomplex z );  // C++ only
```

### <a name="parameters"></a>參數

*z*<br/>
代表指數的複數。

## <a name="return-value"></a>傳回值

**E**的值，從*z*的乘冪。

## <a name="remarks"></a>備註

因為C++允許多載，所以您可以呼叫採用並傳回 **_Fcomplex**和 **_Lcomplex**值之**cexp**的多載。 在 C 程式中， **cexp**一律會接受並傳回 **_Dcomplex**值。

## <a name="requirements"></a>需求

|常式傳回的值|C 標頭|C++ 標頭|
|-------------|--------------|------------------|
|**cexp**、 **cexpf**、 **cexpl**|\<complex.h>|\<complex.h>|

如需相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
[cpow、cpowf、cpowl](cpow-cpowf-cpowl.md)<br/>
[clog10、clog10f、clog10l](clog10-clog10f-clog10l.md)<br/>
[clog、clogf、clogl](clog-clogf-clogl.md)<br/>
