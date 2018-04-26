---
title: asin、asinf、asinl | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- asinf
- asinl
- asin
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
- asin
- asinl
- asinf
dev_langs:
- C++
helpviewer_keywords:
- asin function
- asinl function
- asinf function
- trigonometric functions
- arcsine function
ms.assetid: ca05f9ea-b711-49f6-9f32-2f4019abfd69
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6dd1399042e1055d124cd3c53363a6979d4256d3
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="asin-asinf-asinl"></a>asin、asinf、asinl

計算反正弦值。

## <a name="syntax"></a>語法

```C
double asin( double x );
float asinf ( float x );
long double asinl( long double x );
```

```cpp
float asin( float x );  // C++ only
long double asin( long double x );  // C++ only
```

### <a name="parameters"></a>參數

*x*<br/>
要計算的反正弦值。

## <a name="return-value"></a>傳回值

**Asin**函式會傳回的反正弦值 （數值的反正弦值函式） *x*範圍-π/2 到 π/2 弧度中。

根據預設，如果*x*小於-1 或大於 1， **asin**傳回無限期。

|輸入|SEH 例外狀況|Matherr 例外狀況|
|-----------|-------------------|-----------------------|
|± ∞|**無效**|**_DOMAIN**|
|± **QNAN**， **IND**|無|**_DOMAIN**|
|&#124;x&#124;>1|**無效**|**_DOMAIN**|

## <a name="remarks"></a>備註

因為 c + + 允許多載，所以您可以呼叫的多載**asin**與**float**和**長** **double**值。 在 C 程式中， **asin**一律採用並傳回**double**。

## <a name="requirements"></a>需求

|常式|必要的標頭 (C)|必要的標頭 (C++)|
|-------------|---------------------|-|
|**asin**， **asinf**， **asinl**|\<math.h>|\<cmath> 或 \<math.h>|

## <a name="example"></a>範例

如需詳細資訊，請參閱 [acos、acosf、acosl](acos-acosf-acosl.md)。

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[acos、acosf、acosl](acos-acosf-acosl.md)<br/>
[atan、atanf、atanl、atan2、atan2f、atan2l](atan-atanf-atanl-atan2-atan2f-atan2l.md)<br/>
[cos、cosf、cosl](cos-cosf-cosl.md)<br/>
[_matherr](matherr.md)<br/>
[sin、sinf、sinl](sin-sinf-sinl.md)<br/>
[tan、tanf、tanl](tan-tanf-tanl.md)<br/>
