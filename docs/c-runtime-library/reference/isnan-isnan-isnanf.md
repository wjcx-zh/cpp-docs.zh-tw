---
title: isnan、_isnan、_isnanf
ms.date: 01/31/2019
apiname:
- _isnan
- _isnanf
- isnan
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
ms.openlocfilehash: 8a907dd33803cebd7bc5d71789834d115333b6a0
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/04/2019
ms.locfileid: "55703086"
---
# <a name="isnan-isnan-isnanf"></a>isnan、_isnan、_isnanf

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

在 C 中， **isnan**巨集並 **_isnan**並 **_isnanf**函式會傳回非零值，如果引數*x*為 nan，否則為它們傳回 0。

C + + **isnan**函式會傳回 **，則為 true**如果引數*x*為 NaN; 否則會傳回**false**。

## <a name="remarks"></a>備註

因為 NaN 值不會比較為等於其他的 NaN 值，您必須使用其中一種函數或巨集，以偵測站台。 無法在指定之類型的 IEEE-754 浮點數格式表示浮點運算的結果時，會產生 NaN。 如需如何為 NaN 輸出中表示的資訊，請參閱[printf](printf-printf-l-wprintf-wprintf-l.md)。

當編譯為 c + + **isnan**巨集未定義，以及**isnan**改為定義的範本函式。 它的行為方式與巨集，但傳回值的型別**bool**而不是整數。

**_Isnan**並 **_isnanf**是 Microsoft 特有的函式。 **_Isnanf**函式只適用於 x64 編譯時。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭 (C)|必要的標頭 (C++)|
|-------------|---------------------------|-------------------------------|
|**isnan**， **_isnanf**|\<math.h>|\<math.h> 或 \<cmath>|
|**_isnan**|\<float.h>|\<float.h> 或 \<cfloat>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass、_fpclassf](fpclass-fpclassf.md)<br/>
[isfinite _finite、 _finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnormal](isnormal.md)<br/>
