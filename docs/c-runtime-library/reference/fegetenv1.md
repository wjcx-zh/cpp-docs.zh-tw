---
title: fegetenv
ms.date: 04/05/2018
api_name:
- fetegenv
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
- fegetenv
- fenv/fegetenv
helpviewer_keywords:
- fetegenv function
ms.assetid: 68962421-6978-4b27-8e4c-ad1577830cf6
ms.openlocfilehash: b2e3566eb96174d0f0ccd6beb401824cc052c995
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941238"
---
# <a name="fegetenv"></a>fegetenv

將目前的浮點環境儲存在指定的物件中。

## <a name="syntax"></a>語法

```C
int fegetenv(
   fenv_t *penv
);
```

### <a name="parameters"></a>參數

*penv*<br/>
要包含目前浮點環境值之**fenv_t**物件的指標。

## <a name="return-value"></a>傳回值

如果已成功將浮點環境儲存在*penv*中，則會傳回0。 否則，傳回非零值。

## <a name="remarks"></a>備註

**Fegetenv**函數會將目前的浮點環境儲存在*penv*所指向的物件中。 浮點點環境是一組會影響浮點計算的狀態旗標和控制項模式。 這包括捨入方向模式以及處理浮點例外狀況的狀態旗標。  如果*penv*未指向有效的**fenv_t**物件，則不會定義後續的行為。

若要使用此函式，您必須在呼叫之前使用 `#pragma fenv_access(on)` 指示詞，以關閉可能會妨礙存取的浮點最佳化作業。 如需詳細資訊，請參閱 [fenv_access](../../preprocessor/fenv-access.md)。

## <a name="requirements"></a>需求

|函數|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**fegetenv**|\<fenv.h>|\<cfenv>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
[fesetenv](fesetenv1.md)<br/>
