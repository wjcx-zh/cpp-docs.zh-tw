---
title: feraiseexcept
ms.date: 04/05/2018
api_name:
- feraiseexcept
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
- feraiseexcept
- fenv/feraiseexcept
helpviewer_keywords:
- feraiseexcept function
ms.assetid: 87e89151-83c2-4563-9a9a-45666245d437
ms.openlocfilehash: e98c402169ed0f35ab1bdf0b8221a2248f252f21
ms.sourcegitcommit: ba4180a2d79d7e391f2f705797505d4aedbc2a5e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2020
ms.locfileid: "76972216"
---
# <a name="feraiseexcept"></a>feraiseexcept

引發指定的浮點例外狀況。

## <a name="syntax"></a>語法

```C
int feraiseexcept(
   int excepts
);
```

### <a name="parameters"></a>參數

*以外*<br/>
要引發的浮點例外狀況。

## <a name="return-value"></a>傳回值

如果成功引發所有指定的例外狀況，則傳回 0。

## <a name="remarks"></a>備註

**Feraiseexcept**函數會嘗試引發*以外*所指定的浮點例外狀況。   **Feraiseexcept**函式支援在 \<fenv.h 中定義的這些例外狀況宏 >：

|例外狀況巨集|描述|
|---------------------|-----------------|
|FE_DIVBYZERO|在稍早的浮點運算中發生的獨一性或極錯誤，已建立無限大值。|
|FE_INEXACT|函式已強制四捨五入稍早的浮點運算預存結果。|
|FE_INVALID|在稍早的浮點運算中發生的網域錯誤。|
|FE_OVERFLOW|發生範圍錯誤，稍早的浮點運算結果太大，無法表示。|
|FE_UNDERFLOW|稍早的浮點運算結果太小，無法以完整精確度表示；已建立 denormal 值。|
|FE_ALL_EXCEPT|所有受支援浮點例外狀況的位元 OR。|

*以外*引數可以是零、其中一個例外狀況宏值，或是兩個或多個受支援例外狀況宏的位 or。 如果其中一個指定的例外狀況巨集是 FE_OVERFLOW 或 FE_UNDERFLOW，則可能會發生副作用 FE_INEXACT 例外狀況。

若要使用此函式，您必須在呼叫之前使用 `#pragma fenv_access(on)` 指示詞，以關閉可能會妨礙存取的浮點最佳化作業。 如需詳細資訊，請參閱 [fenv_access](../../preprocessor/fenv-access.md)。

**Microsoft 特定：** 在*以外*中指定的例外狀況會依照 order FE_INVALID、FE_DIVBYZERO、FE_OVERFLOW、FE_UNDERFLOW、FE_INEXACT 順序來引發。 不過，即使在*以外*中未指定，也會在引發 FE_OVERFLOW 或 FE_UNDERFLOW 時引發 FE_INEXACT。

## <a name="requirements"></a>需求

|函數|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|*feraiseexcept*|\<fenv.h>|\<cfenv>|

如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>
[feholdexcept](feholdexcept2.md)<br/>
[fetestexcept](fetestexcept1.md)<br/>
[feupdateenv](feupdateenv.md)<br/>
