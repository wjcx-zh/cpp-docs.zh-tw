---
title: fesetenv |Microsoft 文件
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
- fesetenv
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
- fesetenv
- fenv/fesetenv
dev_langs:
- C++
helpviewer_keywords:
- fesetenv function
ms.assetid: ffc64fff-8ea7-4d59-9e04-ff96ef8cd012
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 466d37a55cbd0d4fdf3e1fc0eed085cb9fcb5b6a
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
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
指標**fenv_t**物件，其中包含所設定的浮點數的環境，藉由呼叫[fegetenv](fegetenv1.md)或[feholdexcept](feholdexcept2.md)。 您也可以使用指定的預設啟動浮點環境**FE_DFL_ENV**巨集。

## <a name="return-value"></a>傳回值

如果成功設定環境，則傳回 0。 否則，傳回非零值。

## <a name="remarks"></a>備註

**Fesetenv**函式會將目前的浮點環境中儲存的值從**fenv_t**指向的物件*penv*。 浮點點環境是一組會影響浮點計算的狀態旗標和控制項模式。 這包括捨入模式以及處理浮點例外狀況的狀態旗標。  如果*penv*不**FE_DFL_ENV**或未指向有效**fenv_t**物件，後續的行為是未定義。

呼叫此函式設定的例外狀況中的狀態旗標*penv*物件，但它不會引發這些例外狀況。

若要使用此函式，您必須在呼叫之前使用 `#pragma fenv_access(on)` 指示詞，以關閉可能會妨礙存取的浮點最佳化作業。 如需詳細資訊，請參閱 [fenv_access](../../preprocessor/fenv-access.md)。

## <a name="requirements"></a>需求

|功能|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**fesetenv**|\<fenv.h>|\<cfenv>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
[fegetenv](fegetenv1.md)<br/>
[feclearexcept](feclearexcept1.md)<br/>
[feholdexcept](feholdexcept2.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>
