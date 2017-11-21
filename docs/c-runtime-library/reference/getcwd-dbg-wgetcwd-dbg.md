---
title: "_getcwd_dbg、_wgetcwd_dbg | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wgetcwd_dbg
- _getcwd_dbg
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
- api-ms-win-crt-environment-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _getcwd_dbg
- _wgetcwd_dbg
- getcwd_dbg
- wgetcwd_dbg
dev_langs: C++
helpviewer_keywords:
- wgetcwd_dbg function
- working directory
- _getcwd_dbg function
- getcwd_dbg function
- current working directory
- _wgetcwd_dbg function
- directories [C++], current working
ms.assetid: 8d5d151f-d844-4aa6-a28c-1c11a22dc00d
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 286404a87680f50be5311250643925488eff88e6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="getcwddbg-wgetcwddbg"></a>_getcwd_dbg、_wgetcwd_dbg
偵錯版本的 [_getdcwd、_wgetdcwd](../../c-runtime-library/reference/getcwd-wgetcwd.md) 函式 (僅於偵錯期間可供使用)。  
  
## <a name="syntax"></a>語法  
  
```  
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
  
#### <a name="parameters"></a>參數  
 `buffer`  
 路徑的儲存位置。  
  
 `maxlen`  
 路徑的最大長度 (以字元為單位)：`char` 的 `_getcwd_dbg`，以及 `wchar_t` 的 `_wgetcwd_dbg`。  
  
 `blockType`  
 要求的記憶體區塊類型：`_CLIENT_BLOCK` 或 `_NORMAL_BLOCK`。  
  
 `filename`  
 要求配置作業之原始程式檔的名稱的指標，或為 `NULL`。  
  
 `linenumber`  
 原始程式檔中的行號，其中要求配置作業，或為 `NULL`。  
  
## <a name="return-value"></a>傳回值  
 傳回 `buffer`的指標。 `NULL` 傳回值表示錯誤，且 `errno` 會設定為 `ENOMEM`，表示記憶體不足以配置 `maxlen` 個位元組 (指定 `NULL` 引數給 `buffer`時)，或是設定為 `ERANGE`，表示路徑長度超過 `maxlen` 個字元。  
  
 如需詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>備註  
 `_getcwd_dbg`和`_wgetcwd_dbg`函式完全相同`_getcwd`和`_wgetcwd`不同之處在於，當`_DEBUG`是定義，這些函式使用的偵錯版本`malloc`和`_malloc_dbg`配置記憶體，如果`NULL`當做第一個參數傳遞。 如需詳細資訊，請參閱 [_malloc_dbg](../../c-runtime-library/reference/malloc-dbg.md)。  
  
 在大多數情況中，您不需要明確地呼叫這些函式。 但您可以定義 `_CRTDBG_MAP_ALLOC` 旗標。 定義 `_CRTDBG_MAP_ALLOC` 時，呼叫 `_getcwd` 和 `_wgetcwd` 會分別重新對應至 `_getcwd_dbg` 和 `_wgetcwd_dbg`，且 `blockType` 會設為 `_NORMAL_BLOCK`。 因此，您不需要呼叫這些函式，除非您想要將堆積區塊標示為 `_CLIENT_BLOCK`。 如需詳細資訊，請參閱[偵錯堆積上的區塊類型](/visualstudio/debugger/crt-debug-heap-details)。  
  
## <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tgetcwd_dbg`|`_getcwd_dbg`|`_getcwd_dbg`|`_wgetcwd_dbg`|  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_getcwd_dbg`|\<crtdbg.h>|  
|`_wgetcwd_dbg`|\<crtdbg.h>|  
  
 如需相容性詳細資訊，請參閱簡介中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="see-also"></a>另請參閱  
 [_getcwd、_wgetcwd](../../c-runtime-library/reference/getcwd-wgetcwd.md)   
 [目錄控制](../../c-runtime-library/directory-control.md)   
 [堆積配置函式的偵錯版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)