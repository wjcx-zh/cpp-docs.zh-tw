---
title: _findclose | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _findclose
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _findclose
- findclose
dev_langs:
- C++
helpviewer_keywords:
- _findclose function
- findclose function
ms.assetid: 9216c573-0878-444c-b5d7-cdaf16fb9163
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9a25ed42f1a53eb81c834997f42db0154658f376
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="findclose"></a>_findclose

關閉指定的搜尋控制代碼，並釋出相關聯的資源。

## <a name="syntax"></a>語法

```C
int _findclose(
   intptr_t handle
);
```

### <a name="parameters"></a>參數

*控制代碼*<br/>
先前呼叫所傳回的搜尋控制代碼 **_findfirst**。

## <a name="return-value"></a>傳回值

如果成功的話， **_findclose**傳回 0。 否則，它會傳回-1，並設定**errno**至**ENOENT**，指出沒有相符的檔案，找不到。

## <a name="requirements"></a>需求

|功能|必要的標頭|
|--------------|---------------------|
|**_findclose**|\<io.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[系統呼叫](../../c-runtime-library/system-calls.md)<br/>
[檔案名稱搜尋函式](../../c-runtime-library/filename-search-functions.md)<br/>
