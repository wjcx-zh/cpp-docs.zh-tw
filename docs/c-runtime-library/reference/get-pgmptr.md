---
title: _get_pgmptr | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _get_pgmptr
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
- get_pgmptr
- _get_pgmptr
dev_langs:
- C++
helpviewer_keywords:
- get_pgmptr function
- _get_pgmptr function
- pgmptr global variable
- _pgmptr global variable
ms.assetid: 29f16a9f-a685-4721-add3-7fad4f67eece
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6af6203f8c6f40335a132f21929abf3cc4ce1808
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="getpgmptr"></a>_get_pgmptr

取得目前的值 **_pgmptr**全域變數。

## <a name="syntax"></a>語法

```C
errno_t _get_pgmptr( 
   char **pValue 
);
```

### <a name="parameters"></a>參數

*pValue*<br/>
要填入的目前值的字串指標 **_pgmptr**變數。

## <a name="return-value"></a>傳回值

如果成功，傳回零；如果失敗，則傳回錯誤碼。 如果*pValue*是**NULL**，會叫用無效參數處理常式，如中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，此函式會將**errno**至**EINVAL**並傳回**EINVAL**。

## <a name="remarks"></a>備註

只能呼叫 **_get_pgmptr**如果您的程式具有的窄的進入點，如**main （)** 或**Winmain**。 **_Pgmptr**全域變數包含與處理序相關聯的可執行檔的完整路徑。 如需詳細資訊，請參閱 [_pgmptr、_wpgmptr](../../c-runtime-library/pgmptr-wpgmptr.md)。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_get_pgmptr**|\<stdlib.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[_get_wpgmptr](get-wpgmptr.md)<br/>
