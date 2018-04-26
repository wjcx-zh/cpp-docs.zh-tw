---
title: ceil、ceilf、ceill | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ceilf
- ceil
- ceill
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
- ntdll.dll
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- ceil
- ceilf
- ceill
dev_langs:
- C++
helpviewer_keywords:
- calculating value ceilings
- ceill function
- ceil function
- ceilf function
ms.assetid: f4e5acab-5c8f-4b10-9ae2-9561e6453718
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9fb24817dd4f23e1dac44f49fcf7dbec34a358c1
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="ceil-ceilf-ceill"></a>ceil、ceilf、ceill

計算最大值。

## <a name="syntax"></a>語法

```C
double ceil(
   double x
);
float ceil(
   float x
);  // C++ only
long double ceil(
   long double x
);  // C++ only
float ceilf(
   float x
);
long double ceill(
   long double x
);
```

### <a name="parameters"></a>參數

*x*<br/>
浮點值。

## <a name="return-value"></a>傳回值

**Ceil**函式會傳回表示大於或等於最小整數的浮點值*x*。 不會傳回錯誤。

|輸入|SEH 例外狀況|Matherr 例外狀況|
|-----------|-------------------|-----------------------|
|± **QNAN**， **IND**|無|**_DOMAIN**|

**ceil**有使用 Streaming SIMD Extensions 2 (SSE2) 的實作。 如需使用 SSE2 實作的資訊和限制，請參閱 [_set_SSE2_enable](set-sse2-enable.md)。

## <a name="remarks"></a>備註

因為 c + + 允許多載，所以您可以呼叫的多載**ceil**採用**float**或**長** **double**型別。 在 C 程式中， **ceil**一律採用並傳回**double**。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**ceil**， **ceilf**， **ceill**|\<math.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [floor](floor-floorf-floorl.md) 的範例。

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[floor、floorf、floorl](floor-floorf-floorl.md)<br/>
[fmod、fmodf](fmod-fmodf.md)<br/>
[round、roundf、roundl](round-roundf-roundl.md)<br/>
