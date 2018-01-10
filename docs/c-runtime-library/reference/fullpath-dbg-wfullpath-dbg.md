---
title: "_fullpath_dbg、_wfullpath_dbg | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wfullpath_dbg
- _fullpath_dbg
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
- wfullpath_dbg
- _wfullpath_dbg
- _fullpath_dbg
- fullpath_dbg
dev_langs: C++
helpviewer_keywords:
- _fullpath_dbg function
- relative file paths
- absolute paths
- fullpath_dbg function
- _wfullpath_dbg function
- wfullpath_dbg function
ms.assetid: 81f72f85-07da-4f5c-866a-598e0fb03f6b
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6ca0d3229f539c05817fd9dddc4e8cd30ec5abdb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="fullpathdbg-wfullpathdbg"></a>_fullpath_dbg、_wfullpath_dbg
使用 `malloc` 之偵錯版本來配置記憶體的 [_fullpath、_wfullpath](../../c-runtime-library/reference/fullpath-wfullpath.md) 版本。  
  
## <a name="syntax"></a>語法  
  
```  
char *_fullpath_dbg(   
   char *absPath,  
   const char *relPath,  
   size_t maxLength,  
   int blockType,  
   const char *filename,  
   int linenumber   
);  
wchar_t *_wfullpath_dbg(   
   wchar_t *absPath,  
   const wchar_t *relPath,  
   size_t maxLength,  
   int blockType,  
   const char *filename,  
   int linenumber   
);  
```  
  
#### <a name="parameters"></a>參數  
 `absPath`  
 包含絕對路徑名稱或完整路徑名稱之緩衝區的指標，或為 `NULL`。  
  
 `relPath`  
 相對路徑名稱。  
  
 `maxLength`  
 絕對路徑名稱緩衝區的最大長度 (`absPath`)。 此長度針對 `_fullpath` 使用位元組，但針對 `wchar_t` 使用寬字元 (`_wfullpath`)。  
  
 `blockType`  
 要求的記憶體區塊類型：`_CLIENT_BLOCK` 或 `_NORMAL_BLOCK`。  
  
 `filename`  
 要求配置作業之原始程式檔的名稱的指標，或為 `NULL`。  
  
 `linenumber`  
 原始程式檔中的行號，其中要求配置作業，或為 `NULL`。  
  
## <a name="return-value"></a>傳回值  
 每個函式會傳回包含絕對路徑名稱之緩衝區的指標 (`absPath`)。 若有錯誤 (例如，傳入 `relPath` 的值包含的磁碟機代號無效或是找不到，或是建立的絕對路徑名稱 (`absPath`) 的長度大於 `maxLength`)，函式會傳回 `NULL`。  
  
## <a name="remarks"></a>備註  
 `_fullpath_dbg`和`_wfullpath_dbg`函式完全相同`_fullpath`和`_wfullpath`不同之處在於，當`_DEBUG`是定義，這些函式使用的偵錯版本`malloc`，`_malloc_dbg`來配置記憶體，如果是 NULL當做第一個參數傳遞。 如需 `_malloc_dbg` 之偵錯版本的詳細資訊，請參閱 [_malloc_dbg](../../c-runtime-library/reference/malloc-dbg.md)。  
  
 在大多數情況中，您不需要明確地呼叫這些函式。 但您可以定義 `_CRTDBG_MAP_ALLOC` 旗標。 定義 `_CRTDBG_MAP_ALLOC` 時，呼叫 `_fullpath` 和 `_wfullpath` 會分別重新對應至 `_fullpath_dbg` 和 `_wfullpath_dbg`，且 `blockType` 會設為 `_NORMAL_BLOCK`。 因此，您不需要呼叫這些函式，除非您想要將堆積區塊標示為 `_CLIENT_BLOCK`。 如需詳細資訊，請參閱[偵錯堆積上的區塊類型](/visualstudio/debugger/crt-debug-heap-details)。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tfullpath_dbg`|`_fullpath_dbg`|`_fullpath_dbg`|`_wfullpath_dbg`|  
  
## <a name="requirements"></a>需求  
  
|功能|必要的標頭|  
|--------------|---------------------|  
|`_fullpath_dbg`|\<crtdbg.h>|  
|`_wfullpath_dbg`|\<crtdbg.h>|  
  
 如需相容性詳細資訊，請參閱簡介中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="see-also"></a>請參閱  
 [檔案處理](../../c-runtime-library/file-handling.md)   
 [_fullpath、_wfullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)   
 [堆積配置函式的偵錯版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)