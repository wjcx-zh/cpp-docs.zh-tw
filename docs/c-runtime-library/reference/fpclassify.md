---
title: fpclassify
ms.date: 04/05/2018
api_name:
- fpclassify
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
api_type:
- HeaderDef
f1_keywords:
- fpclassify
- math/fpclassify
helpviewer_keywords:
- fpclassify macro
- fpclassify function
ms.assetid: bf549499-7ff9-4a58-8692-f2d1cb6bab81
ms.openlocfilehash: e9b5aa1f7dc20cc920a51c2c36371eb907469875
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957069"
---
# <a name="fpclassify"></a>fpclassify

傳回引數的浮點分類。

## <a name="syntax"></a>語法

```C
int fpclassify(
   /* floating-point */ x
);

int fpclassify(
   float x
); // C++ only

int fpclassify(
   double x
); // C++ only

int fpclassify(
   long double x
); // C++ only
```

### <a name="parameters"></a>參數

*x*<br/>
要測試的浮點值。

## <a name="return-value"></a>傳回值

**fpclassify**會傳回一個整數值，指出引數*x*的浮點類別。 下表顯示**fpclassify**所傳回的可能值（定義于\<math > 中）。

|值|描述|
|-----------|-----------------|
|**FP_NAN**|無訊息、訊號或不確定的 NaN|
|**FP_INFINITE**|正或負無限大|
|**FP_NORMAL**|正或負標準化非零值|
|**FP_SUBNORMAL**|正或負異常化值|
|**FP_ZERO**|正或負零值|

## <a name="remarks"></a>備註

在 C 中， **fpclassify**是宏;在C++中， **fpclassify**是使用**float**、 **double**或**long** **double**引數類型的多載函式。 在任一情況下，傳回值取決於引數運算式的有效類型，而非任何中繼呈現。 例如，當轉換成**float**時，一般**double**或**long** **double**值可能會變成無限大、denormal 或零值。

## <a name="requirements"></a>需求

|函式/巨集|必要的標頭 (C)|必要的標頭 (C++)|
|---------------------|---------------------------|-------------------------------|
|**fpclassify**|\<math.h>|\<math.h> 或 \<cmath>|

**Fpclassify**宏和**FPCLASSIFY**函數符合 ISO C99 和 c + + 11 規格。 如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[isnan、_isnan、_isnanf](isnan-isnan-isnanf.md)<br/>
