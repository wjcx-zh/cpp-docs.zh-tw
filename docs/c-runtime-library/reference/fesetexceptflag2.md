---
title: fesetexceptflag
ms.date: 04/05/2018
apiname:
- fesetexceptflag
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- fesetexceptflag
- fenv/fesetexceptflag
helpviewer_keywords:
- fesetexceptflag function
ms.assetid: 2f7dad77-9e54-4097-a3e3-35176ace4de5
ms.openlocfilehash: 9ac79e790f0b1e7a89413a0d4974f6053c95616e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50615874"
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
指標**fexcept_t**物件，其中包含將例外狀況狀態旗標設定為值。 物件可能是由先前呼叫 [fegetexceptflag](fegetexceptflag2.md) 所設定。

*removed*<br/>
要設定的浮點例外狀況狀態旗標。

## <a name="return-value"></a>傳回值

如果成功設定所有指定的例外狀況狀態旗標，則傳回 0。 否則，傳回非零值。

## <a name="remarks"></a>備註

**Fesetexceptflag**函式設定所指定的浮點例外狀況狀態旗標的狀態*removed*設定中的對應值**fexcept_t**指向的物件*pstatus*。  它不會引發例外狀況。 *Pstatus*指標必須指向有效**fexcept_t**物件或後續行為是未定義。 **Fesetexceptflag**函式支援這些例外狀況巨集值*removed*，其定義於\<fenv.h >:

|例外狀況巨集|描述|
|---------------------|-----------------|
|FE_DIVBYZERO|在稍早的浮點運算中發生的獨一性或極錯誤，已建立無限大值。|
|FE_INEXACT|函式已強制四捨五入稍早的浮點運算預存結果。|
|FE_INVALID|在稍早的浮點運算中發生的網域錯誤。|
|FE_OVERFLOW|發生範圍錯誤，稍早的浮點運算結果太大，無法表示。|
|FE_UNDERFLOW|稍早的浮點運算結果太小，無法以完整精確度表示；已建立 denormal 值。|
|FE_ALLEXCEPT|所有受支援浮點例外狀況的位元 OR。|

*Removed*引數可以是零，其中一個支援的浮點例外狀況巨集，或位元，或是兩個或以上巨集。 未定義任何其他引數值的效果。

若要使用此函式，您必須在呼叫之前使用 `#pragma fenv_access(on)` 指示詞，以關閉可能會妨礙存取的浮點最佳化作業。 如需詳細資訊，請參閱 [fenv_access](../../preprocessor/fenv-access.md)。

## <a name="requirements"></a>需求

|功能|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**fesetexceptflag**|\<fenv.h>|\<cfenv>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
[fegetexceptflag](fegetexceptflag2.md)<br/>
