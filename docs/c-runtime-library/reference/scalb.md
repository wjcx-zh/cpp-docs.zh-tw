---
title: _scalb，_scalbf |Microsoft 文件
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _scalb
- _scalbf
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
- scalb
- _scalb
- _scalbf
dev_langs:
- C++
helpviewer_keywords:
- exponential calculations
- _scalb function
- _scalbf function
- scalb function
ms.assetid: 148cf5a8-b405-44bf-a1f0-7487adba2421
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f27f0c6ad88a8d0d89ab9bb66ba68eac0625507c
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="scalb-scalbf"></a>_scalb _scalbf

將引數依 2 的乘冪進位。

## <a name="syntax"></a>語法

```C
double _scalb(
   double x,
   long exp
);
float _scalbf(
   float x,
   long exp
); /* x64 only */
```

### <a name="parameters"></a>參數

*x*<br/>
雙精確度浮點值。

*exp*<br/>
長整數指數。

## <a name="return-value"></a>傳回值

如果成功，則傳回指數值。 在溢位 (根據正負號的*x*)， **_scalb**傳回 + /- **HUGE_VAL**; **errno**變數會設為**為 ERANGE**。

如需此傳回碼與其他傳回碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_Scalb**函式計算的值*x* * 2<sup>*exp*</sup>。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_scalb**， **_scalbf**|\<float.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[ldexp](ldexp.md)<br/>
