---
title: clog、clogf、clogl
description: 用於堵塞、clogf 和 clogl 的 API 參考;這會取出複數的自然對數，並沿著負實數軸剪下分支。
ms.date: 11/04/2016
api_name:
- clog
- clogf
- clogl
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
- clog
- clogf
- clogl
- complex/clog
- complex/clogf
- complex/clogl
helpviewer_keywords:
- clog function
- clogf function
- clogl function
ms.assetid: 870b9b0b-6618-46f3-bfcf-da595cbd5e18
ms.openlocfilehash: 255f83a93c5c7a0c724fad143f028c2832be3173
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555068"
---
# <a name="clog-clogf-clogl"></a>clog、clogf、clogl

擷取複數的自然對數，而且負實際軸中有分支部分。

## <a name="syntax"></a>語法

```C
_Dcomplex clog(
   _Dcomplex z
);
_Fcomplex clog(
   _Fcomplex z
);  // C++ only
_Lcomplex clog(
   _Lcomplex z
);  // C++ only
_Fcomplex clogf(
   _Fcomplex z
);
_Lcomplex clogl(
   _Lcomplex z
);
```

### <a name="parameters"></a>參數

*Z*\
對數的底數。

## <a name="return-value"></a>傳回值

*Z*的自然對數。 結果是沿著實際軸和在虛數軸的間隔 [-i π，+ i π] 中未系結。

可能的傳回值如下：

|z 參數|傳回值|
|-----------------|------------------|
|正|z 的底數 10 對數|
|零|- ∞|
|負|NaN|
|NaN|NaN|
|+ ∞|+ ∞|

## <a name="remarks"></a>備註

因為 c + + 允許多載，所以您可以呼叫採用並傳回 **_Fcomplex**和 **_Lcomplex**值的**堵塞**多載。 在 C 程式中， **阻塞** 一律會採用並傳回 **_Dcomplex** 值。

## <a name="requirements"></a>規格需求

|常式傳回的值|C 標頭|C++ 標頭|
|-------------|--------------|------------------|
|**阻塞**、               **clogf**、 **clogl**|\<complex.h>|\<ccomplex>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函數參考](crt-alphabetical-function-reference.md)<br/>
[cexp、cexpf、cexpl](cexp-cexpf-cexpl.md)<br/>
[cpow、cpowf、cpowl](cpow-cpowf-cpowl.md)<br/>
[clog10、clog10f、clog10l](clog10-clog10f-clog10l.md)<br/>
