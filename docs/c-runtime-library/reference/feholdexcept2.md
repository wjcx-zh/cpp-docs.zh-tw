---
title: feholdexcept
ms.date: 04/05/2018
api_name:
- feholdexcept
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
- feholdexcept
- fenv/feholdexcept
helpviewer_keywords:
- feholdexcept function
ms.assetid: 88e512ae-b5d8-452c-afe9-c824cd3ef1d8
ms.openlocfilehash: bd55a4ed627d731f7246d589d4b74b4173e31d4e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941193"
---
# <a name="feholdexcept"></a>feholdexcept

將目前的浮點環境儲存在指定的物件中、清除浮點狀態旗標，以及可能的話，將浮點環境放入連續模式中。

## <a name="syntax"></a>語法

```C
int feholdexcept(
   fenv_t *penv
);
```

### <a name="parameters"></a>參數

*penv*<br/>
要包含浮點環境複本之**fenv_t**物件的指標。

## <a name="return-value"></a>傳回值

只有在函式能夠成功開啟非停止浮點例外狀況處理時，才傳回零。

## <a name="remarks"></a>備註

**Feholdexcept**函數是用來將目前浮點環境的狀態儲存在*penv*所指向的**fenv_t**物件中，並將環境設定為不會在浮點例外狀況上中斷執行。 這稱之為連續模式。  此模式會繼續執行，直到使用 [fesetenv](fesetenv1.md) 或 [feupdateenv](feupdateenv.md) 還原環境為止。

您可以在需要隱藏呼叫端一或多個浮點例外狀況的副程式開頭使用此函式。 若要回報例外狀況，您可以使用 feclearexcept 清除不想要的例外狀況[，](feclearexcept1.md)然後在呼叫**feupdateenv**時結束非停止模式。

若要使用此函式，您必須在呼叫之前使用 `#pragma fenv_access(on)` 指示詞，以關閉可能會妨礙存取的浮點最佳化作業。 如需詳細資訊，請參閱 [fenv_access](../../preprocessor/fenv-access.md)。

## <a name="requirements"></a>需求

|函數|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**feholdexcept**|\<fenv.h>|\<cfenv>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
[feclearexcept](feclearexcept1.md)<br/>
[fesetenv](fesetenv1.md)<br/>
[feupdateenv](feupdateenv.md)<br/>
