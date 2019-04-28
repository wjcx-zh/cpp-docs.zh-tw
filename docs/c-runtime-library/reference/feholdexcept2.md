---
title: feholdexcept
ms.date: 04/05/2018
apiname:
- feholdexcept
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
- feholdexcept
- fenv/feholdexcept
helpviewer_keywords:
- feholdexcept function
ms.assetid: 88e512ae-b5d8-452c-afe9-c824cd3ef1d8
ms.openlocfilehash: 26097398b9f9d498ab4c56690dc9c6cbb950bafb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62334381"
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
指標**fenv_t**物件，以包含浮點環境的複本。

## <a name="return-value"></a>傳回值

才能夠順利開啟連續浮點例外狀況處理函式，是的則傳回零。

## <a name="remarks"></a>備註

**Feholdexcept**函式用來儲存目前浮點環境中的狀態**fenv_t**指向物件*penv*，同時將環境設定為不會中斷執行浮點例外狀況。 這稱之為連續模式。  此模式會繼續執行，直到使用 [fesetenv](fesetenv1.md) 或 [feupdateenv](feupdateenv.md) 還原環境為止。

您可以在需要隱藏呼叫端一或多個浮點例外狀況的副程式開頭使用此函式。 若要回報例外狀況，只要清除不想要的例外狀況使用[feclearexcept](feclearexcept1.md)然後結束連續模式下，呼叫**feupdateenv**。

若要使用此函式，您必須在呼叫之前使用 `#pragma fenv_access(on)` 指示詞，以關閉可能會妨礙存取的浮點最佳化作業。 如需詳細資訊，請參閱 [fenv_access](../../preprocessor/fenv-access.md)。

## <a name="requirements"></a>需求

|功能|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**feholdexcept**|\<fenv.h>|\<cfenv>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
[feclearexcept](feclearexcept1.md)<br/>
[fesetenv](fesetenv1.md)<br/>
[feupdateenv](feupdateenv.md)<br/>
