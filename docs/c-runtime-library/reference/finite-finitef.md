---
title: isfinite _finite、 _finitef
ms.date: 01/31/2019
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
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- isfinite
- finite
- _finite
- _finitef
- math/isfinite
- math/_finite
- math/_finitef
- float/_finite
helpviewer_keywords:
- finite function
- _finite function
- _finitef function
ms.assetid: 5a7d7ca7-befb-4e1f-831d-28713c6eb805
ms.openlocfilehash: d727839521978be66c3dc9ee173ee2ba0a567445
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210376"
---
# <a name="isfinite-finite-finitef"></a>isfinite _finite、 _finitef

判斷指定的浮點數值是否有限。

## <a name="syntax"></a>語法

```C
int isfinite(
   /* floating-point */ x
); /* C-only macro */

template <class FloatingType>
inline bool isfinite(
   FloatingType x
) throw(); /* C++-only template function */

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

`isfinite`巨集和`_finite`並`_finitef`函式會傳回非零值，如果*x*是正常或 subnormal 有限值。 它們會傳回 0，如果引數為無限或 NaN。 C + + 內嵌樣板函式`isfinite`相同的行為，但會傳回 **，則為 true**或是**false**。

## <a name="remarks"></a>備註

`isfinite` 是當編譯為 C 和內嵌範本函式編譯為 c + + 時，巨集。 `_finite`和`_finitef`是 Microsoft 特有的函式。 只有在針對 x86、ARM 或 ARM64 平台進行編譯時，才能使用 `_finitef` 函式。

## <a name="requirements"></a>需求

|功能|必要的標頭 (C)|必要的標頭 (C++)|
|--------------|---------------------------|-------------------------------|
|`_finite`|\<float.h> 或 \<math.h>|\<float.h>、\<math.h>、\<cfloat> 或 \<cmath>|
|`isfinite`、 `_finitef`|\<math.h>|\<math.h> 或 \<cmath>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass、_fpclassf](fpclass-fpclassf.md)<br/>
[isinf](isinf.md)<br/>
[isnan、_isnan、_isnanf](isnan-isnan-isnanf.md)<br/>
[isnormal](isnormal.md)<br/>
