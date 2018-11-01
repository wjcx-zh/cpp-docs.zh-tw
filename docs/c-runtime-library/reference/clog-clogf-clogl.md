---
title: clog、clogf、clogl
ms.date: 11/04/2016
apiname:
- clog
- clogf
- clogl
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
ms.openlocfilehash: fcbc9ba7984898d51f7a3d0beb5ef7c8b6d6892c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50636549"
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

*z*<br/>
對數的底數。

## <a name="return-value"></a>傳回值

自然對數*z*。 結果是在實數軸，並在間隔中未繫結 [-i π，+ i π] 在虛數軸。

可能的傳回值如下：

|z 參數|傳回值|
|-----------------|------------------|
|正|z 的底數 10 對數|
|零|- ∞|
|負|NaN|
|NaN|NaN|
|+ ∞|+ ∞|

## <a name="remarks"></a>備註

因為 c + + 允許多載，您可以呼叫多載**clog**採用並傳回 **_Fcomplex**並 **_Lcomplex**值。 在 C 程式中， **clog**一律採用並傳回 **_Dcomplex**值。

## <a name="requirements"></a>需求

|常式傳回的值|C 標頭|C++ 標頭|
|-------------|--------------|------------------|
|**clog**， **clogf**， **clogl**|\<complex.h>|\<ccomplex>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
[cexp、cexpf、cexpl](cexp-cexpf-cexpl.md)<br/>
[cpow、cpowf、cpowl](cpow-cpowf-cpowl.md)<br/>
[clog10、clog10f、clog10l](clog10-clog10f-clog10l.md)<br/>
