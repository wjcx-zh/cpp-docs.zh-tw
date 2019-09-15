---
title: _getcwd_dbg、_wgetcwd_dbg
ms.date: 11/04/2016
api_name:
- _wgetcwd_dbg
- _getcwd_dbg
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
- api-ms-win-crt-environment-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _getcwd_dbg
- _wgetcwd_dbg
- getcwd_dbg
- wgetcwd_dbg
helpviewer_keywords:
- wgetcwd_dbg function
- working directory
- _getcwd_dbg function
- getcwd_dbg function
- current working directory
- _wgetcwd_dbg function
- directories [C++], current working
ms.assetid: 8d5d151f-d844-4aa6-a28c-1c11a22dc00d
ms.openlocfilehash: 3eb318b9b2faa8716abdd26eafa926c8072b5614
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955285"
---
# <a name="_getcwd_dbg-_wgetcwd_dbg"></a>_getcwd_dbg、_wgetcwd_dbg

偵錯版本的 [_getdcwd、_wgetdcwd](getcwd-wgetcwd.md) 函式 (僅於偵錯期間可供使用)。

## <a name="syntax"></a>語法

```C
char *_getcwd_dbg(
   char *buffer,
   int maxlen,
   int blockType,
   const char *filename,
   int linenumber
);
wchar_t *_wgetcwd_dbg(
   wchar_t *buffer,
   int maxlen,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>參數

*buffer*<br/>
路徑的儲存位置。

*maxlen*<br/>
路徑的最大長度（以字元為單位）： **char**代表 **_getcwd_dbg** ，而**wchar_t**代表 **_wgetcwd_dbg**。

*blockType*<br/>
要求的記憶體區塊類型： **_CLIENT_BLOCK**或 **_NORMAL_BLOCK**。

*filename*<br/>
要求配置作業之原始程式檔的名稱的指標，或為**Null**。

*linenumber*<br/>
原始程式檔中的行號，其中要求配置作業，或**為 Null**。

## <a name="return-value"></a>傳回值

傳回*緩衝區*的指標。 **Null**傳回值表示錯誤，並將**Errno**設定為**ENOMEM**，表示記憶體不足，無法配置*maxlen*位元組（當**Null**引數指定為*buffer*時）或**ERANGE**，表示路徑長度超過*maxlen*個字元。

如需詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_Getcwd_dbg**和 **_wgetcwd_dbg**函式與 **_getcwd**和 **_wgetcwd**相同，不同之處在于，當已定義 **_debug**時，這些函式會使用的 DEBUG 版本**malloc**和 **_malloc_dbg**如果傳遞**Null**做為第一個參數，則配置記憶體。 如需詳細資訊，請參閱 [_malloc_dbg](malloc-dbg.md)。

在大多數情況中，您不需要明確地呼叫這些函式。 相反地，您可以定義 **_CRTDBG_MAP_ALLOC**旗標。 當定義 **_CRTDBG_MAP_ALLOC**時， **_getcwd**和 **_wgetcwd**的呼叫會分別重新對應至 **_getcwd_dbg**和 **_wgetcwd_dbg**，並將*blockType*設定為 **_NORMAL_BLOCK**。 因此，您不需要明確呼叫這些函式，除非您想要將堆積區塊標記為 **_CLIENT_BLOCK**。 如需詳細資訊，請參閱[偵錯堆積上的區塊類型](/visualstudio/debugger/crt-debug-heap-details)。

## <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetcwd_dbg**|**_getcwd_dbg**|**_getcwd_dbg**|**_wgetcwd_dbg**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_getcwd_dbg**|\<crtdbg.h>|
|**_wgetcwd_dbg**|\<crtdbg.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[_getcwd、_wgetcwd](getcwd-wgetcwd.md)<br/>
[目錄控制](../../c-runtime-library/directory-control.md)<br/>
[堆積配置函式的偵錯版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
