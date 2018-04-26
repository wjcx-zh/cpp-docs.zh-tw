---
title: imaxdiv | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- imaxdiv
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
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- imaxdiv
dev_langs:
- C++
helpviewer_keywords:
- imaxdiv function
ms.assetid: 7d90126f-fdc2-4986-9cdf-94e4c9123d26
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ab39d68f733fdb7d078efdc058f09e30d0fd907b
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="imaxdiv"></a>imaxdiv

以單一作業計算任何大小之兩個整數值的商數和餘數。

## <a name="syntax"></a>語法

```C
imaxdiv_t imaxdiv(
   intmax_t numer,
   intmax_t denom
);
```

### <a name="parameters"></a>參數

*numer*<br/>
分子。

*denom*<br/>
分母。

## <a name="return-value"></a>傳回值

**imaxdiv**的型別引數呼叫[intmax_t](../../c-runtime-library/standard-types.md)傳回型別的結構[imaxdiv_t](../../c-runtime-library/standard-types.md) ，包含商和餘數。

## <a name="remarks"></a>備註

**Imaxdiv**函式除以*numer*由*denom* ，並藉此計算商數及餘數。 **Imaxdiv_t**結構包含商數**intmax_t** **q u o t**，其餘部分，及**intmax_t** **rem**.商數的正負號與數學商數相同。 其絕對值是小於數學商數絕對值的最大整數。 如果分母為 0，程式會終止並出現錯誤訊息。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**imaxdiv**|\<inttypes.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_imaxdiv.c
// Build using: cl /W3 /Tc crt_imaxdiv.c
// This example takes two integers as command-line
// arguments and calls imaxdiv to divide the first
// argument by the second, then displays the results.

#include <stdio.h>
#include <stdlib.h>
#include <inttypes.h>

int main(int argc, char *argv[])
{
   intmax_t x,y;
   imaxdiv_t div_result;

   x = atoll(argv[1]);
   y = atoll(argv[2]);

   printf("The call to imaxdiv(%lld, %lld)\n", x, y);
   div_result = imaxdiv(x, y);
   printf("results in a quotient of %lld, and a remainder of %lld\n\n",
          div_result.quot, div_result.rem);
}
```

建置後以命令列參數 `9460730470000000 8766` 呼叫，程式碼會產生以下輸出︰

```Output
The call to imaxdiv(9460730470000000, 8766)
results in a quotient of 1079252848505, and a remainder of 5170
```

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[div](div.md)<br/>
[ldiv、lldiv](ldiv-lldiv.md)<br/>
