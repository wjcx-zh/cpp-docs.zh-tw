---
title: _finite、_finitef | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _finite
- _finitef
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
- finite
- _finite
- _finitef
- math/_finite
- math/_finitef
- float/_finite
dev_langs:
- C++
helpviewer_keywords:
- finite function
- _finite function
- _finitef function
ms.assetid: 5a7d7ca7-befb-4e1f-831d-28713c6eb805
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 31b34568def8969fea3602e749502beceb989b39
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="finite-finitef"></a>_finite、_finitef

判斷指定的浮點數值是否有限。

## <a name="syntax"></a>語法

```C
int _finite(
   double x
);

int _finitef(
   float x
); /* x64 and ARM/ARM64 only */
```

### <a name="parameters"></a>參數

*x*<br/>
要測試的浮點值。

## <a name="return-value"></a>傳回值

同時 **_finite**和 **_finitef**傳回非零值，如果引數*x*為有限; 也就是說，如果-INF < *x* < + INF。 如果引數為無限或 NAN，它會傳回 0。

## <a name="remarks"></a>備註

**_Finite**和 **_finitef**函式是 Microsoft 專有的。 **_Finitef**函式只是針對 x86、 ARM、 或 ARM64 編譯時，才能使用平台。

## <a name="requirements"></a>需求

|功能|必要的標頭 (C)|必要的標頭 (C++)|
|--------------|---------------------------|-------------------------------|
|**_finite**|\<float.h> 或 \<math.h>|\<float.h>、\<math.h>、\<cfloat> 或 \<cmath>|
|**_finitef**|\<math.h>|\<math.h> 或 \<cmath>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[isnan、_isnan、_isnanf](isnan-isnan-isnanf.md)<br/>
[_fpclass、_fpclassf](fpclass-fpclassf.md)<br/>
