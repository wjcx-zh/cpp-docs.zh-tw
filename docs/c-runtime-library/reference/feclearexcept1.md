---
title: feclearexcept1
ms.date: 04/05/2018
apiname:
- feclearexcept
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
- feclearexcept
- fenv/feclearexcept
helpviewer_keywords:
- feclearexcept function
ms.assetid: ef419da3-c248-4432-b53c-8e7a475d9533
ms.openlocfilehash: 3c2f037a5be903fc006debfa7319c483431fdd92
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62334732"
---
# <a name="feclearexcept"></a>feclearexcept

嘗試清除引數指定的浮點例外狀況旗標。

## <a name="syntax"></a>語法

```C
int feclearexcept(
   int excepts
);
```

### <a name="parameters"></a>參數

*excepts*<br/>
要清除的例外狀況狀態旗標。

## <a name="return-value"></a>傳回值

傳回零，如果*removed*為零，或如果已順利清除所有指定的例外狀況。 否則，傳回非零值。

## <a name="remarks"></a>備註

**Feclearexcept**函式嘗試清除浮點點所指定的例外狀況狀態旗標*removed*。 函式支援這些在 fenv.h 中定義的例外狀況巨集︰

|例外狀況巨集|描述|
|---------------------|-----------------|
|FE_DIVBYZERO|在稍早的浮點運算中發生的獨一性或極錯誤，已建立無限大值。|
|FE_INEXACT|函式已強制四捨五入稍早的浮點運算預存結果。|
|FE_INVALID|在稍早的浮點運算中發生的網域錯誤。|
|FE_OVERFLOW|發生範圍錯誤，稍早的浮點運算結果太大，無法表示。|
|FE_UNDERFLOW|稍早的浮點運算結果太小，無法以完整精確度表示；已建立 denormal 值。|
|FE_ALL_EXCEPT|所有受支援浮點例外狀況的位元 OR。|

*Removed*引數可以是零或一或多個受支援例外狀況巨集的位元 OR。 未定義任何其他引數值的結果。

## <a name="requirements"></a>需求

|功能|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**feclearexcept**|\<fenv.h>|\<cfenv>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
[fetestexcept](fetestexcept1.md)<br/>
