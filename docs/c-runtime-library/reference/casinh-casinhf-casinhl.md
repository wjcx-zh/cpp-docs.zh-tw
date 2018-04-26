---
title: casinh、casinhf、casinhl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- casinh
- casinhl
- casinhf
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
- casinh
- casinhf
- casinhl
- complex/casinh
- complex/casinhf
- complex/casinhl
dev_langs:
- C++
helpviewer_keywords:
- casinh function
- casinhf function
- casinhl function
ms.assetid: bd18340b-21dd-4c86-a14e-e8e15dd97e3b
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 71f57f097ae66b6849bf3c2bd532c39d02aae2b3
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="casinh-casinhf-casinhl"></a>casinh、casinhf、casinhl

擷取與分支剪下間隔外部的複數的反雙曲正弦 [-i + 我] 軸虛數。

## <a name="syntax"></a>語法

```C
_Dcomplex casinh(
   _Dcomplex z
);
_Fcomplex casinh(
   _Fcomplex z
);  // C++ only
_Lcomplex casinh(
   _Lcomplex z
);  // C++ only
_Fcomplex casinhf(
   _Fcomplex z
);
_Lcomplex casinhl(
   _Lcomplex z
);
```

### <a name="parameters"></a>參數

*z*<br/>
代表角度的複數 (弧度)。

## <a name="return-value"></a>傳回值

反雙曲正弦*z*，以弧度為單位。 結果是在實際的軸和間隔中未繫結 [-iπ/2 + iπ/2] 的虛數座標軸。

## <a name="remarks"></a>備註

因為 c + + 允許多載，所以您可以呼叫的多載**casinh**採用並傳回 **_Fcomplex**和 **_Lcomplex**值。 在 C 程式中， **casinh**一律採用並傳回 **_Dcomplex**值。

## <a name="requirements"></a>需求

|常式|C 標頭|C++ 標頭|
|-------------|--------------|------------------|
|**casinh**， **casinhf**， **casinhl**|\<complex.h>|\<ccomplex>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
[catanh、catanhf、catanhl](catanh-catanhf-catanhl.md)<br/>
[ctanh、ctanhf、ctanhl](ctanh-ctanhf-ctanhl.md)<br/>
[catan、catanf、catanl](catan-catanf-catanl.md)<br/>
[csinh、csinhf、csinhl](csinh-csinhf-csinhl.md)<br/>
[ccosh、ccoshf、ccoshl](ccosh-ccoshf-ccoshl.md)<br/>
[cacosh、cacoshf、cacoshl](cacosh-cacoshf-cacoshl.md)<br/>
[cacos、cacosf、cacosl](cacos-cacosf-cacosl.md)<br/>
[ctan、ctanf、ctanl](ctan-ctanf-ctanl.md)<br/>
[csin、csinf、csinl](csin-csinf-csinl.md)<br/>
[casin、casinf、casinl](casin-casinf-casinl.md)<br/>
[ccos、ccosf、ccosl](ccos-ccosf-ccosl.md)<br/>
[csqrt、csqrtf、csqrtl](csqrt-csqrtf-csqrtl.md)<br/>
