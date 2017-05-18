---
title: "_strdup_dbg、_wcsdup_dbg | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _strdup_dbg
- _wcsdup_dbg
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
- _wcsdup_dbg
- strdup_dbg
- _strdup_dbg
- wcsdup_dbg
dev_langs:
- C++
helpviewer_keywords:
- _wcsdup_dbg function
- stdup_dbg function
- copying strings
- duplicating strings
- strings [C++], copying
- strings [C++], duplicating
- _strdup_dbg function
- wcsdup_dbg function
ms.assetid: 681db70c-d124-43ab-b83e-5eeea9035097
caps.latest.revision: 11
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 477fca0e1849099502acea0b5d5a17fb00622b35
ms.contentlocale: zh-tw
ms.lasthandoff: 03/30/2017

---
# <a name="strdupdbg-wcsdupdbg"></a>_strdup_dbg、_wcsdup_dbg
使用偵錯版本的 `malloc` 的 [_strdup 和 _wcsdup](../../c-runtime-library/reference/strdup-wcsdup-mbsdup.md) 版本。  
  
## <a name="syntax"></a>語法  
  
```  
char *_strdup_dbg(  
   const char *strSource,  
   int blockType,  
   const char *filename,  
   int linenumber   
);  
wchar_t *_wcsdup_dbg(  
   const wchar_t *strSource,  
   int blockType,  
   const char *filename,  
   int linenumber   
);  
```  
  
#### <a name="parameters"></a>參數  
 `strSource`  
 以 Null 結束的來源字串。  
  
 `blockType`  
 要求的記憶體區塊類型：`_CLIENT_BLOCK` 或 `_NORMAL_BLOCK`。  
  
 `filename`  
 要求配置作業之原始程式檔的名稱的指標，或為 NULL。  
  
 `linenumber`  
 原始程式檔中的行號，其中要求配置作業，或為 NULL。  
  
## <a name="return-value"></a>傳回值  
 這些函式全都會傳回所複製字串之儲存位置的指標，或是在無法配置儲存區時，傳回 `NULL` 。  
  
## <a name="remarks"></a>備註  
 `_strdup_dbg` 和 `_wcsdup_dbg` 函式與 `_strdup` 和 `_wcsdup` 相同，唯一不同的是當定義 `_DEBUG` 時，這些函式會使用偵錯版本的 `malloc` 和 `_malloc_dbg` 來配置所複製字串的記憶體。 如需 `_malloc_dbg` 之偵錯功能的資訊，請參閱 [_malloc_dbg](../../c-runtime-library/reference/malloc-dbg.md)。  
  
 在大多數情況中，您不需要明確地呼叫這些函式。 但您可以定義 `_CRTDBG_MAP_ALLOC` 旗標。 定義 `_CRTDBG_MAP_ALLOC` 時，呼叫 `_strdup` 和 `_wcsdup` 會分別重新對應至 `_strdup_dbg` 和 `_wcsdup_dbg`，且 `blockType` 會設為 `_NORMAL_BLOCK`。 因此，您不需要呼叫這些函式，除非您想要將堆積區塊標示為 `_CLIENT_BLOCK`。 如需區塊類型的詳細資訊，請參閱[偵錯堆積上的區塊類型](/visualstudio/debugger/crt-debug-heap-details)。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcsdup_dbg`|`_strdup_dbg`|`_mbsdup`|`_wcsdup_dbg`|  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_strdup_dbg`, `_wcsdup_dbg`|\<crtdbg.h>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>程式庫  
 所有偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="see-also"></a>另請參閱  
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [_strdup、_wcsdup、_mbsdup](../../c-runtime-library/reference/strdup-wcsdup-mbsdup.md)   
 [堆積配置函式的偵錯版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)
