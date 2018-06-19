---
title: fegetenv |Microsoft 文件
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- fetegenv
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
- fegetenv
- fenv/fegetenv
dev_langs:
- C++
helpviewer_keywords:
- fetegenv function
ms.assetid: 68962421-6978-4b27-8e4c-ad1577830cf6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fc8b5d189838c2788bc6200f9072c9511e61d42f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32396166"
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
指標**fenv_t**包含目前的浮點環境值的物件。

## <a name="return-value"></a>傳回值

傳回 0 表示浮點環境已成功儲存在*penv*。 否則，傳回非零值。

## <a name="remarks"></a>備註

**Fegetenv**函式會將目前的浮點環境所指向的物件存放至*penv*。 浮點點環境是一組會影響浮點計算的狀態旗標和控制項模式。 這包括捨入方向模式以及處理浮點例外狀況的狀態旗標。  如果*penv*並未指向有效**fenv_t**物件，後續的行為是未定義。

若要使用此函式，您必須在呼叫之前使用 `#pragma fenv_access(on)` 指示詞，以關閉可能會妨礙存取的浮點最佳化作業。 如需詳細資訊，請參閱 [fenv_access](../../preprocessor/fenv-access.md)。

## <a name="requirements"></a>需求

|功能|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**fegetenv**|\<fenv.h>|\<cfenv>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
[fesetenv](fesetenv1.md)<br/>
