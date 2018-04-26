---
title: fegetexceptflag |Microsoft 文件
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- fegetexceptflag
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
- fegetexceptflag
- fenv/fegetexceptflag
dev_langs:
- C++
helpviewer_keywords:
- fegetexceptflag function
ms.assetid: 2d28f0ca-70c9-4cff-be8b-3d876eacde71
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5f81f89b6e004ff188b381ec38e3af6ef3d7585d
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="fegetexceptflag"></a>fegetexceptflag

儲存目前的指定浮點例外狀況旗標的狀態。

## <a name="syntax"></a>語法

```C
int fegetexceptflag(
   fexcept_t* pstatus,
   int excepts
);

```

### <a name="parameters"></a>參數

*pstatus*<br/>
指標**fexcept_t**物件，以包含所指定的例外狀況旗標的目前值*excepts*。

*excepts*<br/>
浮點例外狀況旗標，以存放*pstatus*。

## <a name="return-value"></a>傳回值

成功時會傳回 0。 否則，傳回非零值。

## <a name="remarks"></a>備註

**Fegetexceptflag**函式將所指定的浮點例外狀況狀態旗標的目前狀態儲存*excepts*中**fexcept_t**指向的物件*pstatus*。  *pstatus*必須指向有效**fexcept_t**物件或後續的行為是未定義。 **Fegetexceptflag**函式可支援定義在這些例外狀況巨集\<fenv.h >:

|例外狀況巨集|描述|
|---------------------|-----------------|
|FE_DIVBYZERO|在稍早的浮點運算中發生的獨一性或極錯誤，已建立無限大值。|
|FE_INEXACT|函式已強制四捨五入稍早的浮點運算預存結果。|
|FE_INVALID|在稍早的浮點運算中發生的網域錯誤。|
|FE_OVERFLOW|發生範圍錯誤，稍早的浮點運算結果太大，無法表示。|
|FE_UNDERFLOW|稍早的浮點運算結果太小，無法以完整精確度表示；已建立 denormal 值。|
|FE_ALLEXCEPT|所有受支援浮點例外狀況的位元 OR。|

*Excepts*引數可以是零，其中一種支援的浮點例外狀況巨集，或位元或兩個或多個巨集。 未定義任何其他引數值的效果。

若要使用此函式，您必須在呼叫之前使用 `#pragma fenv_access(on)` 指示詞，以關閉可能會妨礙存取的浮點最佳化作業。 如需詳細資訊，請參閱 [fenv_access](../../preprocessor/fenv-access.md)。

## <a name="requirements"></a>需求

|功能|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**fegetexceptflag**|\<fenv.h>|\<cfenv>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>
