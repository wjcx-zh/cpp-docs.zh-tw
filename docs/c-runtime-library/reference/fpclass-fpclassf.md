---
title: _fpclass、_fpclassf
ms.date: 4/2/2020
api_name:
- _fpclass
- _fpclassf
- _o__fpclass
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fpclass
- _fpclass
- _fpclassf
- math/_fpclass
- float/_fpclass
- math/_fpclassf
helpviewer_keywords:
- fpclass function
- floating-point numbers, IEEE representation
- _fpclass function
- _fpclassf function
ms.assetid: 2774872d-3543-446f-bc72-db85f8b95a6b
ms.openlocfilehash: b16655fed046114e9dd8592c5e1fd3fc5f7ed4bf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346282"
---
# <a name="_fpclass-_fpclassf"></a>_fpclass、_fpclassf

傳回一個值，指出引數的浮點分類。

## <a name="syntax"></a>語法

```C
int _fpclass(
   double x
);

int _fpclassf(
   float x
); /* x64 only */
```

### <a name="parameters"></a>參數

*X.*<br/>
要測試的浮點值。

## <a name="return-value"></a>傳回值

**_fpclass**和 **_fpclassf**函數返回一個整數值,指示參數*x*的浮點分類。 分類可能會有 \<float.h> 中所定義的下列其中一個值。

|值|描述|
|-----------|-----------------|
|**_FPCLASS_SNAN**|訊號 NaN|
|**_FPCLASS_QNAN**|無訊息 NaN|
|**_FPCLASS_NINF**|負無窮大 (-INF)|
|**_FPCLASS_NN**|負標準化非零|
|**_FPCLASS_ND**|負異常化|
|**_FPCLASS_NZ**|負零 (- 0)|
|**_FPCLASS_PZ**|正 0 (+0)|
|**_FPCLASS_PD**|正異常化|
|**_FPCLASS_PN**|正標準化非零|
|**_FPCLASS_PINF**|正無限大 (+INF)|

## <a name="remarks"></a>備註

**_fpclass**和 **_fpclassf**功能特定於 Microsoft。 它們與 [fpclassify](fpclassify.md) 類似，但傳回引數的更多詳細資訊。 僅當為 x64 平台編譯時 **,_fpclassf**功能才可用。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|函式|必要的標頭|
|--------------|---------------------|
|**_fpclass**, **_fpclassf**|\<float.h>|

如需相容性和一致性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[isnan、_isnan、_isnanf](isnan-isnan-isnanf.md)<br/>
[fpclassify](fpclassify.md)<br/>
