---
title: fetestexcept
ms.date: 04/05/2018
api_name:
- fetestexcept
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fetestexcept
- fenv/fetestexcept
helpviewer_keywords:
- fetestexept function
ms.assetid: ca4dc43f-5573-440d-bc19-ead7571b13dc
ms.openlocfilehash: e70ae1b74420b8186cccd8fc8a817423df618adf
ms.sourcegitcommit: ba4180a2d79d7e391f2f705797505d4aedbc2a5e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2020
ms.locfileid: "76972153"
---
# <a name="fetestexcept"></a>fetestexcept

決定目前設定哪一個指定的浮點例外狀況狀態旗標。

## <a name="syntax"></a>語法

```C
int fetestexcept(
   int excepts
);
```

### <a name="parameters"></a>參數

*以外*<br/>
要測試的浮點狀態旗標位元 OR。

## <a name="return-value"></a>傳回值

成功時會傳回包含浮點例外狀況巨集位元 OR 的遮罩設定，這些巨集對應目前設定的例外狀況狀態旗標。 如未設定任何例外狀況，則傳回 0。

## <a name="remarks"></a>備註

使用 fetestexcept 函式判斷浮點運算引發的例外狀況。 使用*以外*參數來指定要測試的例外狀況狀態旗標。 **Fetestexcept**函式會使用在*以外*中 \<fenv.h. h > 中定義的這些例外狀況宏和傳回值：

|例外狀況巨集|描述|
|---------------------|-----------------|
|FE_DIVBYZERO|在稍早的浮點運算中發生的獨一性或極錯誤，已建立無限大值。|
|FE_INEXACT|函式已強制四捨五入稍早的浮點運算預存結果。|
|FE_INVALID|在稍早的浮點運算中發生的網域錯誤。|
|FE_OVERFLOW|發生範圍錯誤，稍早的浮點運算結果太大，無法表示。|
|FE_UNDERFLOW|稍早的浮點運算結果太小，無法以完整精確度表示；已建立 denormal 值。|
|FE_ALL_EXCEPT|所有受支援浮點例外狀況的位元 OR。|

指定的*以外*引數可以是0、其中一個支援的浮點例外狀況宏，或是兩個或多個宏的位 or。 任何其他*以外*引數值的效果尚未定義。

若要使用此函式，您必須在呼叫之前使用 `#pragma fenv_access(on)` 指示詞，以關閉可能會妨礙存取的浮點最佳化作業。 如需詳細資訊，請參閱 [fenv_access](../../preprocessor/fenv-access.md)。

## <a name="requirements"></a>需求

|函數|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**fetestexcept**|\<fenv.h>|\<cfenv>|

如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
[feclearexcept](feclearexcept1.md)<br/>
[feraiseexcept](feraiseexcept.md)<br/>
