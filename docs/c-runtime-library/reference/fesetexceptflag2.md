---
title: fesetexceptflag
ms.date: 04/05/2018
api_name:
- fesetexceptflag
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
- fesetexceptflag
- fenv/fesetexceptflag
helpviewer_keywords:
- fesetexceptflag function
ms.assetid: 2f7dad77-9e54-4097-a3e3-35176ace4de5
ms.openlocfilehash: b16de7ea54b5f1df21b6626febe773c8cef556f5
ms.sourcegitcommit: ba4180a2d79d7e391f2f705797505d4aedbc2a5e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2020
ms.locfileid: "76972150"
---
# <a name="fesetexceptflag"></a>fesetexceptflag

在目前的浮點環境中設定指定的浮點狀態旗標。

## <a name="syntax"></a>語法

```C
int fesetexceptflag(
     const fexcept_t *pstatus,
     int excepts
);
```

### <a name="parameters"></a>參數

*pstatus*<br/>
**Fexcept_t**物件的指標，其中包含要設定例外狀況狀態旗標的值。 物件可能是由先前呼叫 [fegetexceptflag](fegetexceptflag2.md) 所設定。

*以外*<br/>
要設定的浮點例外狀況狀態旗標。

## <a name="return-value"></a>傳回值

如果成功設定所有指定的例外狀況狀態旗標，則傳回 0。 否則，傳回非零值。

## <a name="remarks"></a>備註

**Fesetexceptflag**函數會將*以外*所指定之浮點例外狀況狀態旗標的狀態，設定為*pstatus*所指向之**fexcept_t**物件中所設定的對應值。  它不會引發例外狀況。 *Pstatus*指標必須指向有效的**fexcept_t**物件，否則不會定義後續的行為。 **Fesetexceptflag**函數支援*以外*中的這些例外狀況宏值，定義于 \<fenv.h 中 >：

|例外狀況巨集|描述|
|---------------------|-----------------|
|FE_DIVBYZERO|在稍早的浮點運算中發生的獨一性或極錯誤，已建立無限大值。|
|FE_INEXACT|函式已強制四捨五入稍早的浮點運算預存結果。|
|FE_INVALID|在稍早的浮點運算中發生的網域錯誤。|
|FE_OVERFLOW|發生範圍錯誤，稍早的浮點運算結果太大，無法表示。|
|FE_UNDERFLOW|稍早的浮點運算結果太小，無法以完整精確度表示；已建立 denormal 值。|
|FE_ALL_EXCEPT|所有受支援浮點例外狀況的位元 OR。|

*以外*引數可以是零、其中一個支援的浮點例外狀況宏，或是兩個或多個宏的位 or。 未定義任何其他引數值的效果。

若要使用此函式，您必須在呼叫之前使用 `#pragma fenv_access(on)` 指示詞，以關閉可能會妨礙存取的浮點最佳化作業。 如需詳細資訊，請參閱 [fenv_access](../../preprocessor/fenv-access.md)。

## <a name="requirements"></a>需求

|函數|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**fesetexceptflag**|\<fenv.h>|\<cfenv>|

如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
[fegetexceptflag](fegetexceptflag2.md)<br/>
