---
title: fesetenv
ms.date: 04/05/2018
api_name:
- fesetenv
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
- fesetenv
- fenv/fesetenv
helpviewer_keywords:
- fesetenv function
ms.assetid: ffc64fff-8ea7-4d59-9e04-ff96ef8cd012
ms.openlocfilehash: 155b9f635f6e8c3dc5acb61126f41c49cd32601f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941116"
---
# <a name="fesetenv"></a>fesetenv

設定目前的浮點環境。

## <a name="syntax"></a>語法

```C
int fesetenv(
   const fenv_t *penv
);
```

### <a name="parameters"></a>參數

*penv*<br/>
**Fenv_t**物件的指標，其中包含以[fegetenv](fegetenv1.md)或[feholdexcept](feholdexcept2.md)的呼叫所設定的浮點環境。 您也可以使用**FE_DFL_ENV**宏來指定預設啟動浮點環境。

## <a name="return-value"></a>傳回值

如果成功設定環境，則傳回 0。 否則，傳回非零值。

## <a name="remarks"></a>備註

**Fesetenv**函數會從*penv*所指向的**fenv_t**物件中儲存的值，設定目前的浮點環境。 浮點點環境是一組會影響浮點計算的狀態旗標和控制項模式。 這包括捨入模式以及處理浮點例外狀況的狀態旗標。  如果*penv*不是**FE_DFL_ENV**或不是指向有效的**fenv_t**物件，則不會定義後續的行為。

呼叫此函式會設定*penv*物件中的例外狀況狀態旗標，但不會引發這些例外狀況。

若要使用此函式，您必須在呼叫之前使用 `#pragma fenv_access(on)` 指示詞，以關閉可能會妨礙存取的浮點最佳化作業。 如需詳細資訊，請參閱 [fenv_access](../../preprocessor/fenv-access.md)。

## <a name="requirements"></a>需求

|函數|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**fesetenv**|\<fenv.h>|\<cfenv>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
[fegetenv](fegetenv1.md)<br/>
[feclearexcept](feclearexcept1.md)<br/>
[feholdexcept](feholdexcept2.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>
