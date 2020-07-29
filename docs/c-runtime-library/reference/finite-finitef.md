---
title: isfinite、_finite、_finitef
ms.date: 01/31/2019
api_name:
- _finite
- _finitef
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 7e15a6619e584ff52c07048fcf591835b799587f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218698"
---
# <a name="isfinite-_finite-_finitef"></a>isfinite、_finite、_finitef

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

`isfinite` `_finite` `_finitef` 如果*x*是標準或偏低的有限值，宏和和函數會傳回非零值。 如果引數為無限或 NaN，則會傳回0。 C + + 內嵌範本函式 `isfinite` 的行為相同，但會傳回 **`true`** 或 **`false`** 。

## <a name="remarks"></a>備註

`isfinite`當編譯成 C 時，是一個宏，而當編譯為 c + + 時，是內嵌的範本函式。 `_finite`和函 `_finitef` 式是 Microsoft 特有的。 只有在針對 x86、ARM 或 ARM64 平台進行編譯時，才能使用 `_finitef` 函式。

## <a name="requirements"></a>需求

|函式|必要的標頭 (C)|必要的標頭 (C++)|
|--------------|---------------------------|-------------------------------|
|`_finite`|\<float.h> 或 \<math.h>|\<float.h>、\<math.h>、\<cfloat> 或 \<cmath>|
|`isfinite`, `_finitef`|\<math.h>|\<math.h> 或 \<cmath>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass、_fpclassf](fpclass-fpclassf.md)<br/>
[isinf](isinf.md)<br/>
[isnan、_isnan、_isnanf](isnan-isnan-isnanf.md)<br/>
[isnormal](isnormal.md)<br/>
