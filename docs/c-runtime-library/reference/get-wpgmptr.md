---
title: _get_wpgmptr | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _get_wpgmptr
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
- get_wpgmptr
- _get_wpgmptr
dev_langs:
- C++
helpviewer_keywords:
- _wpgmptr global variable
- get_wpgmptr function
- wpgmptr global variable
- _get_wpgmptr function
ms.assetid: a77cdd13-2303-4b7c-9a60-8debdbef2011
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 23ebeed5b6710a7c8032f75b8677b09f8f96c84a
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="getwpgmptr"></a>_get_wpgmptr

取得目前的值 **_wpgmptr**全域變數。

## <a name="syntax"></a>語法

```C
errno_t _get_wpgmptr( 
   wchar_t **pValue 
);
```

### <a name="parameters"></a>參數

*pValue*<br/>
要填入的目前值的字串指標 **_wpgmptr**變數。

## <a name="return-value"></a>傳回值

如果成功，傳回零；如果失敗，則傳回錯誤碼。 如果*pValue*是**NULL**，會叫用無效參數處理常式，如中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，此函式會將**errno**至**EINVAL**並傳回**EINVAL**。

## <a name="remarks"></a>備註

只能呼叫 **_get_wpgmptr**如果您的程式有廣泛的進入點，如**wmain()** 或**wWinMain()**。 **_Wpgmptr**全域變數包含寬字元字串的處理序相關聯的可執行檔的完整路徑。 如需詳細資訊，請參閱 [_pgmptr、_wpgmptr](../../c-runtime-library/pgmptr-wpgmptr.md)。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_get_wpgmptr**|\<stdlib.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[_get_pgmptr](get-pgmptr.md)<br/>
