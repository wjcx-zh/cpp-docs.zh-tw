---
title: _findclose
ms.date: 11/04/2016
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
helpviewer_keywords:
- _findclose function
- findclose function
ms.assetid: 9216c573-0878-444c-b5d7-cdaf16fb9163
ms.openlocfilehash: 29010f8a502d463eeb6ca98837a1b7dae9f5ae6b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62333751"
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

*handle*<br/>
先前呼叫所傳回的搜尋控制代碼 **_findfirst**。

## <a name="return-value"></a>傳回值

如果成功， **_findclose**會傳回 0。 否則，它會傳回-1，並設定**errno**來**ENOENT**，指出沒有其他比對的檔案，找不到。

## <a name="requirements"></a>需求

|功能|必要的標頭|
|--------------|---------------------|
|**_findclose**|\<io.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[系統呼叫](../../c-runtime-library/system-calls.md)<br/>
[檔案名稱搜尋函式](../../c-runtime-library/filename-search-functions.md)<br/>
