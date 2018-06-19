---
title: catanh、catanhf、catanhl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- catanh
- catanhf
- catanhl
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
- catanh
- catanhf
- catanhl
- complex/catanh
- complex/catanhf
- complex/catanhl
dev_langs:
- C++
helpviewer_keywords:
- catanh function
- catanhf function
- catanhl function
ms.assetid: 1b6021cb-647a-41b4-9d7f-919cc8b57b86
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cd74d00e7f5be5e7631bc33fb9b7ea13eb32a407
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32393946"
---
# <a name="catanh-catanhf-catanhl"></a>catanh、catanhf、catanhl

擷取與實際的軸間隔 [-1; + 1] 以外的分支剪下複數的反雙曲正切。

## <a name="syntax"></a>語法

```C
_Dcomplex catanh(
   _Dcomplex z
);
_Fcomplex catanh(
   _Fcomplex z
);  // C++ only
_Lcomplex catanh(
   _Lcomplex z
);  //  C++ only
_Fcomplex catanhf(
   _Fcomplex z
);
_Lcomplex catanhl(
   _Lcomplex z
);
```

### <a name="parameters"></a>參數

*z*<br/>
代表角度的複數 (弧度)。

## <a name="return-value"></a>傳回值

反雙曲正切*z*，以弧度為單位。 結果是在實際的軸和間隔中未繫結 [-iπ/2; + iπ/2] 的虛數座標軸。 如果會發生網域錯誤*z*超出間隔 [-1，+ 1]。 如果會發生柵欄錯誤*z*為-1 或 + 1。

## <a name="remarks"></a>備註

因為 c + + 允許多載，所以您可以呼叫的多載**catanh**採用並傳回 **_Fcomplex**和 **_Lcomplex**值。 在 C 程式中， **catanh**一律採用並傳回 **_Dcomplex**值。

## <a name="requirements"></a>需求

|常式|C 標頭|C++ 標頭|
|-------------|--------------|------------------|
|**catanh**， **catanhf**， **catanhl**|\<complex.h>|\<ccomplex>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
[ctanh、ctanhf、ctanhl](ctanh-ctanhf-ctanhl.md)<br/>
[catan、catanf、catanl](catan-catanf-catanl.md)<br/>
[csinh、csinhf、csinhl](csinh-csinhf-csinhl.md)<br/>
[casinh、casinhf、casinhl](casinh-casinhf-casinhl.md)<br/>
[ccosh、ccoshf、ccoshl](ccosh-ccoshf-ccoshl.md)<br/>
[cacosh、cacoshf、cacoshl](cacosh-cacoshf-cacoshl.md)<br/>
[cacos、cacosf、cacosl](cacos-cacosf-cacosl.md)<br/>
[ctan、ctanf、ctanl](ctan-ctanf-ctanl.md)<br/>
[csin、csinf、csinl](csin-csinf-csinl.md)<br/>
[casin、casinf、casinl](casin-casinf-casinl.md)<br/>
[ccos、ccosf、ccosl](ccos-ccosf-ccosl.md)<br/>
[csqrt、csqrtf、csqrtl](csqrt-csqrtf-csqrtl.md)<br/>
