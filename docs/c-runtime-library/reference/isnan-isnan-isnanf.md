---
title: isnan、_isnan、_isnanf
ms.date: 01/31/2019
api_name:
- _isnan
- _isnanf
- isnan
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _isnan
- isnan
- math/isnan
- math/_isnan
- math/_isnanf
- _isnanf
helpviewer_keywords:
- NAN (not a number)
- _isnan function
- IEEE floating-point representation
- Not a Number (NANs)
- isnan function
ms.assetid: 391fbc5b-89a4-4fba-997e-68f1131caf82
ms.openlocfilehash: a0cc60fb80f8d5b78ec2947a87fde82a536b413c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953756"
---
# <a name="isnan-_isnan-_isnanf"></a>isnan、_isnan、_isnanf

測試浮點值是否為非數字 (NAN)。

## <a name="syntax"></a>語法

```C
int isnan(
   /* floating-point */ x
); /* C-only macro */

int _isnan(
   double x
);

int _isnanf(
   float x
); /* x64 only */

template <class T>
bool isnan(
   T x
) throw(); /* C++ only */
```

### <a name="parameters"></a>參數

*x*<br/>
要測試的浮點值。

## <a name="return-value"></a>傳回值

在 C 中，如果引數*x*是 NAN，則**isnan**宏和 **_isnan**和 **_isnanf**函數會傳回非零值;否則會傳回0。

在C++中，如果引數*x*是 NaN， **isnan**範本函數會傳回**true** ;否則會傳回**false**。

## <a name="remarks"></a>備註

因為 NaN 值不會與任何其他 NaN 值相等，所以您必須使用這些函數或宏的其中一個來偵測一個。 當浮點運算的結果無法以 IEEE-754 浮點格式表示指定的類型時，就會產生 NaN。 如需如何針對輸出表示 NaN 的詳細資訊，請參閱[printf](printf-printf-l-wprintf-wprintf-l.md)。

當編譯為C++時，不會定義**isnan**宏，而是改為定義**isnan**樣板函式。 其行為與宏相同，但會傳回**bool**類型的值，而不是整數。

**_Isnan**和 **_isnanf**函式是 Microsoft 特有的功能。 只有針對 x64 編譯時，才可以使用 **_isnanf**函數。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭 (C)|必要的標頭 (C++)|
|-------------|---------------------------|-------------------------------|
|**isnan**、 **_isnanf**|\<math.h>|\<math.h> 或 \<cmath>|
|**_isnan**|\<float.h>|\<float.h> 或 \<cfloat>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass、_fpclassf](fpclass-fpclassf.md)<br/>
[isfinite、_finite、_finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnormal](isnormal.md)<br/>
