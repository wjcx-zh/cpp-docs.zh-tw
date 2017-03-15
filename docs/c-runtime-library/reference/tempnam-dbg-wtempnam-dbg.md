---
title: "_tempnam_dbg、_wtempnam_dbg | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wtempnam_dbg
- _tempnam_dbg
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
- wtempnam_dbg
- tempnam_dbg
- _tempnam_dbg
- _wtempnam_dbg
dev_langs:
- C++
helpviewer_keywords:
- file names [C++], creating temporary
- tempnam_dbg function
- temporary files, creating
- file names [C++], temporary
- wtempnam_dbg function
- _tempnam_dbg function
- _wtempnam_dbg function
ms.assetid: e3760bb4-bb01-4808-b689-2c45af56a170
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 4f407dce7825a593273206ada02680d6da99e9a0
ms.lasthandoff: 02/24/2017

---
# <a name="tempnamdbg-wtempnamdbg"></a>_tempnam_dbg、_wtempnam_dbg
使用 `malloc, _malloc_dbg` 偵錯版本的 [_tempnam、_wtempnam、tmpnam、_wtmpnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md) 函式版本。  
  
## <a name="syntax"></a>語法  
  
```  
char *_tempnam_dbg(  
   const char *dir,  
   const char *prefix,  
   int blockType,  
   const char *filename,  
   int linenumber   
);  
wchar_t *_wtempnam_dbg(  
   const wchar_t *dir,  
   const wchar_t *prefix,  
   int blockType,  
   const char *filename,  
   int linenumber   
);  
```  
  
#### <a name="parameters"></a>參數  
 `dir`  
 若沒有 TMP 環境變數，或是 TMP 不是有效的目錄時，檔案名稱中所使用的路徑。  
  
 `prefix`  
 此字串會加在 `_tempnam` 所傳回的名稱前面。  
  
 `blockType`  
 要求的記憶體區塊類型：`_CLIENT_BLOCK` 或 `_NORMAL_BLOCK`。  
  
 `filename`  
 要求配置作業之原始程式檔的名稱的指標，或為 `NULL`。  
  
 `linenumber`  
 原始程式檔中的行號，其中要求配置作業，或為 `NULL`。  
  
## <a name="return-value"></a>傳回值  
 若發生失敗，每個函式均會傳回產生的名稱的指標或 `NULL`。 若 TMP 環境變數和 `dir` 參數中指定了無效的目錄名稱，就會發生失敗。  
  
> [!NOTE]
> 不需要針對  `free` 和 `free_dbg` 配置的指標呼叫 `_tempnam_dbg` (或 `_wtempnam_dbg`)。  
  
## <a name="remarks"></a>備註  
 `_tempnam_dbg` 和 `_wtempnam_dbg` 函式與 `_tempnam` 和 `_wtempnam` 相同，唯一不同的是當定義 `_DEBUG` 時，若 `NULL` 是作為第一個參數進行傳遞，這些函式會使用偵錯版本的 `malloc` 和 `_malloc_dbg` 來配置記憶體。 如需詳細資訊，請參閱 [_malloc_dbg](../../c-runtime-library/reference/malloc-dbg.md)。  
  
 在大多數情況中，您不需要明確地呼叫這些函式。 但您可以定義 `_CRTDBG_MAP_ALLOC` 旗標。 定義 `_CRTDBG_MAP_ALLOC` 時，呼叫 `_tempnam` 和 `_wtempnam` 會分別重新對應至 `_tempnam_dbg` 和 `_wtempnam_dbg`，且 `blockType` 會設為 `_NORMAL_BLOCK`。 因此，您不需要呼叫這些函式，除非您想要將堆積區塊標示為 `_CLIENT_BLOCK`。 如需詳細資訊，請參閱[偵錯堆積上的區塊類型](/visualstudio/debugger/crt-debug-heap-details)。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_ttempnam_dbg`|`_tempnam_dbg`|`_tempnam_dbg`|`_wtempnam_dbg`|  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_tempnam_dbg`, `_wtempnam_dbg`|\<crtdbg.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="net-framework-equivalent"></a>.NET Framework 同等  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另請參閱  
 [_tempnam、_wtempnam、tmpnam、_wtmpnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)   
 [資料流 I/O](../../c-runtime-library/stream-i-o.md)   
 [堆積配置函式的偵錯版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)
