---
title: fpclassify | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.topic: reference
apiname:
- fpclassify
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
apitype: HeaderDef
f1_keywords:
- fpclassify
- math/fpclassify
helpviewer_keywords:
- fpclassify macro
- fpclassify function
ms.assetid: bf549499-7ff9-4a58-8692-f2d1cb6bab81
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: da55cb87804d178d5a305ed466aa498de4bc1ee5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32398428"
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

**fpclassify**傳回整數值，指出引數的浮點數的類別*x*。 下表顯示可能的值傳回**fpclassify**，定義在\<math.h >。

|值|描述|
|-----------|-----------------|
|**FP_NAN**|無訊息、訊號或不確定的 NaN|
|**FP_INFINITE**|正或負無限大|
|**FP_NORMAL**|正或負標準化非零值|
|**FP_SUBNORMAL**|正或負異常化值|
|**FP_ZERO**|正或負零值|

## <a name="remarks"></a>備註

在 C 中， **fpclassify**是巨集; c + + **fpclassify**是使用引數類型的多載函式**float**， **double**，或**長** **double**。 在任一情況下，傳回值取決於引數運算式的有效類型，而非任何中繼呈現。 例如，一般**double**或**長****雙**值會是無限值、 異常，或零值時轉換成**float**。

## <a name="requirements"></a>需求

|函式/巨集|必要的標頭 (C)|必要的標頭 (C++)|
|---------------------|---------------------------|-------------------------------|
|**fpclassify**|\<math.h>|\<math.h> 或 \<cmath>|

**Fpclassify**巨集和**fpclassify**函式符合 ISO C99 與 C + + 11 規格。 如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[isnan、_isnan、_isnanf](isnan-isnan-isnanf.md)<br/>
