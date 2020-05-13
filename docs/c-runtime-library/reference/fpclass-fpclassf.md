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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: a6591d9348739d27831785a05f4a602aacdd4d0c
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914853"
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

*x*<br/>
要測試的浮點值。

## <a name="return-value"></a>傳回值

**_Fpclass**和 **_fpclassf**函式會傳回整數值，指出引數*x*的浮點分類。 分類可能會有 \<float.h> 中所定義的下列其中一個值。

|值|描述|
|-----------|-----------------|
|**_FPCLASS_SNAN**|訊號 NaN|
|**_FPCLASS_QNAN**|無訊息 NaN|
|**_FPCLASS_NINF**|負無限大（-INF）|
|**_FPCLASS_NN**|負標準化非零|
|**_FPCLASS_ND**|負異常化|
|**_FPCLASS_NZ**|負零（-0）|
|**_FPCLASS_PZ**|正 0 (+0)|
|**_FPCLASS_PD**|正異常化|
|**_FPCLASS_PN**|正標準化非零|
|**_FPCLASS_PINF**|正無限大 (+INF)|

## <a name="remarks"></a>備註

**_Fpclass**和 **_fpclassf**函式為 Microsoft 特有的功能。 它們與 [fpclassify](fpclassify.md) 類似，但傳回引數的更多詳細資訊。 只有在針對 x64 平臺進行編譯時，才能使用 **_fpclassf**函數。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|函式|必要的標頭|
|--------------|---------------------|
|**_fpclass**， **_fpclassf**|\<float.h>|

如需相容性和一致性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[isnan、_isnan、_isnanf](isnan-isnan-isnanf.md)<br/>
[fpclassify](fpclassify.md)<br/>
