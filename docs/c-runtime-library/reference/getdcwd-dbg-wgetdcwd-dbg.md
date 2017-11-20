---
title: "_getdcwd_dbg、_wgetdcwd_dbg | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _getdcwd_dbg
- _wgetdcwd_dbg
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
apitype: DLLExport
f1_keywords:
- _getdcwd_dbg
- getdcwd_dbg
- _wgetdcwd_dbg
- wgetdcwd_dbg
dev_langs: C++
helpviewer_keywords:
- working directory
- _getdcwd_dbg function
- wgetdcwd_dbg function
- current working directory
- getdcwd_dbg function
- _wgetdcwd_dbg function
- directories [C++], current working
ms.assetid: 266bf6f0-0417-497f-963d-2e0f306d9385
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8afa6156185ac1d375834bdc22df35f2a94638fd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="getdcwddbg-wgetdcwddbg"></a>_getdcwd_dbg、_wgetdcwd_dbg
偵錯版本的 [_getdcwd、_wgetdcwd](../../c-runtime-library/reference/getdcwd-wgetdcwd.md) 函式 (僅於偵錯期間可供使用)。  
  
## <a name="syntax"></a>語法  
  
```  
char *_getdcwd_dbg(  
   int drive,  
   char *buffer,  
   int maxlen,  
   int blockType,  
   const char *filename,  
   int linenumber   
);  
wchar_t *_wgetdcwd_dbg(  
   int drive,  
   wchar_t *buffer,  
   int maxlen,  
   int blockType,  
   const char *filename,  
   int linenumber   
);  
```  
  
#### <a name="parameters"></a>參數  
 `drive`  
 磁碟機的名稱。  
  
 `buffer`  
 路徑的儲存位置。  
  
 `maxlen`  
 路徑的最大長度 (以字元為單位)：`char` 的 `_getdcwd_dbg`，以及 `wchar_t` 的 `_wgetdcwd_dbg`。  
  
 `blockType`  
 要求的記憶體區塊類型：`_CLIENT_BLOCK` 或 `_NORMAL_BLOCK`。  
  
 `filename`  
 要求配置作業之原始程式檔的名稱的指標，或為 `NULL`。  
  
 `linenumber`  
 原始程式檔中的行號，其中要求配置作業，或為 `NULL`。  
  
## <a name="return-value"></a>傳回值  
 傳回 `buffer`的指標。 `NULL` 傳回值表示錯誤，且 `errno` 會設定為 `ENOMEM`，表示記憶體不足以配置 `maxlen` 個位元組 (指定 `NULL` 引數給 `buffer`時)，或是設定為 `ERANGE`，表示路徑長度超過 `maxlen` 個字元。 如需詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>備註  
 `_getdcwd_dbg` 和 `_wgetdcwd_dbg` 函式與 `_getdcwd` 和 `_wgetdcwd` 相同，唯一不同的是當定義 `_DEBUG` 時，若 `malloc` 是作為 `_malloc_dbg` 參數進行傳遞，這些函式會使用偵錯版本的 `NULL` 和 `buffer` 來配置記憶體。 如需詳細資訊，請參閱 [_malloc_dbg](../../c-runtime-library/reference/malloc-dbg.md)。  
  
 在大多數情況中，您不需要明確地呼叫這些函式。 但您可以定義 `_CRTDBG_MAP_ALLOC` 旗標。 定義 `_CRTDBG_MAP_ALLOC` 時，呼叫 `_getdcwd` 和 `_wgetdcwd` 會分別重新對應至 `_getdcwd_dbg` 和 `_wgetdcwd_dbg`，且 `blockType` 會設為 `_NORMAL_BLOCK`。 因此，您不需要呼叫這些函式，除非您想要將堆積區塊標示為 `_CLIENT_BLOCK`。 如需詳細資訊，請參閱[偵錯堆積上的區塊類型](/visualstudio/debugger/crt-debug-heap-details)。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tgetdcwd_dbg`|`_getdcwd_dbg`|`_getdcwd_dbg`|`_wgetdcwd_dbg`|  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_getdcwd_dbg`|\<crtdbg.h>|  
|`_wgetdcwd_dbg`|\<crtdbg.h>|  
  
 如需相容性詳細資訊，請參閱簡介中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="see-also"></a>另請參閱  
 [_getdcwd、_wgetdcwd](../../c-runtime-library/reference/getdcwd-wgetdcwd.md)   
 [目錄控制](../../c-runtime-library/directory-control.md)   
 [堆積配置函式的偵錯版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)