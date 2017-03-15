---
title: "_findfirst、_findfirst32、_findfirst32i64、_findfirst64、_findfirst64i32、_findfirsti64、_wfindfirst、_wfindfirst32、_wfindfirst32i64、_wfindfirst64、_wfindfirst64i32、_wfindfirsti64 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _findfirst
- _wfindfirst
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
- findfirst32i64
- wfindfirst32i64
- tfindfirst64
- _findfirst64i32
- _wfindfirst32i64
- _wfindfirsti64
- wfindfirst
- _tfindfirsti64
- findfirst32
- _tfindfirst32
- _findfirsti64
- findfirst
- wfindfirst64
- wfindfirst32
- tfindfirst32
- _wfindfirst64i32
- findfirst64i32
- tfindfirst64i32
- _wfindfirst
- findfirsti64
- _findfirst32i64
- wfindfirst64i32
- _wfindfirst32
- _findfirst32
- _tfindfirst32i64
- tfindfirst
- _tfindfirst64i32
- findfirst64
- _tfindfirst
- _findfirst64
- _tfindfirst64
- tfindfirst32i64
- _findfirst
- _wfindfirst64
dev_langs:
- C++
helpviewer_keywords:
- _tfindfirst64 function
- _wfindfirst64i32 function
- _wfindfirst32i64 function
- wfindfirst32 function
- _findfirst function
- wfindfirst64 function
- _wfindfirst function
- _findfirst64i32 function
- wfindfirst function
- _findfirst64 function
- tfindfirst32 function
- _tfindfirst64i32 function
- findfirst function
- findfirst32i64 function
- tfindfirst64 function
- _tfindfirst32 function
- tfindfirst32i64 function
- tfindfirst64i32 function
- _wfindfirsti64 function
- _findfirst32i64 function
- findfirst32 function
- findfirsti64 function
- findfirst64i32 function
- tfindfirsti64 function
- tfindfirst function
- _wfindfirst32 function
- wfindfirsti64 function
- _tfindfirsti64 function
- _tfindfirst function
- _tfindfirst32i64 function
- findfirst64 function
- _findfirst32 function
- _findfirsti64 function
- wfindfirst32i64 function
- wfindfirst64i32 function
- _wfindfirst64 function
ms.assetid: 9bb46d1a-b946-47de-845a-a0b109a33ead
caps.latest.revision: 25
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: f7d0417e6533124cc49e909687d7bc232523c302
ms.lasthandoff: 02/24/2017

---
# <a name="findfirst-findfirst32-findfirst32i64-findfirst64-findfirst64i32-findfirsti64-wfindfirst-wfindfirst32-wfindfirst32i64-wfindfirst64-wfindfirst64i32-wfindfirsti64"></a>_findfirst、_findfirst32、_findfirst32i64、_findfirst64、_findfirst64i32、_findfirsti64、_wfindfirst、_wfindfirst32、_wfindfirst32i64、_wfindfirst64、_wfindfirst64i32、_wfindfirsti64
提供檔名第一個執行個體的資訊，此檔名與 `filespec` 引數中所指定的檔案相符。  
  
## <a name="syntax"></a>語法  
  
```  
intptr_t _findfirst(  
   const char *filespec,  
   struct _finddata_t *fileinfo   
);  
intptr_t _findfirst32(  
   const char *filespec,  
   struct _finddata32_t *fileinfo   
);  
intptr_t _findfirst64(  
   const char *filespec,  
   struct _finddata64_t *fileinfo   
);  
intptr_t _findfirsti64(  
   const char *filespec,  
   struct _finddatai64_t *fileinfo   
);  
intptr_t _findfirst32i64(  
   const char *filespec,  
   struct _finddata32i64_t *fileinfo   
);  
intptr_t _findfirst64i32(  
   const char *filespec,  
   struct _finddata64i32_t *fileinfo   
);  
intptr_t _wfindfirst(  
   const wchar_t *filespec,  
   struct _wfinddata_t *fileinfo   
);  
intptr_t _wfindfirst32(  
   const wchar_t *filespec,  
   struct _wfinddata32_t *fileinfo   
);  
intptr_t _wfindfirst64(  
   const wchar_t *filespec,  
   struct _wfinddata64_t *fileinfo   
);  
intptr_t _wfindfirsti64(  
   const wchar_t *filespec,  
   struct _wfinddatai64_t *fileinfo   
);  
intptr_t _wfindfirst32i64(  
   const wchar_t *filespec,  
   struct _wfinddata32i64_t *fileinfo   
);  
intptr_t _wfindfirst64i32(  
   const wchar_t *filespec,  
   struct _wfinddata64i32_t *fileinfo   
);  
```  
  
#### <a name="parameters"></a>參數  
 `filespec`  
 目標檔案規格 (可以包含萬用字元)。  
  
 `fileinfo`  
 檔案資訊緩衝區。  
  
## <a name="return-value"></a>傳回值  
 如果成功，`_findfirst` 會傳回唯一搜尋控制代碼以識別符合 `filespec` 規格的檔案或檔案群組，這可用於後續 [_findnext](../../c-runtime-library/reference/findnext-functions.md) 或 `_findclose` 呼叫。 否則，`_findfirst` 會傳回 -1，並將 `errno` 設為下列其中一個值。  
  
 `EINVAL`  
 參數無效：`filespec` 或 `fileinfo` 是 `NULL`。 或者，作業系統傳回未預期的錯誤。  
  
 `ENOENT`  
 不相符的檔案規格。  
  
 `ENOMEM`  
 記憶體不足。  
  
 `EINVAL`  
 檔名規格無效，或指定的檔名大於 `MAX_PATH`。  
  
 如需這些傳回碼和其他傳回碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 如果傳入無效參數，則這些函式會叫用無效的參數處理常式 (如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述)。  
  
## <a name="remarks"></a>備註  
 在您完成 `_findfirst` 或 `_findnext` 函式 (或任何變體) 之後，必須呼叫 [_findclose](../../c-runtime-library/reference/findclose.md)。 這會釋放應用程式中這些函式所使用的資源。  
  
 具有 `w` 前置詞的這些函式變化是寬字元版本；否則，它們與對應的單一位元組函式相同。  
  
 這些函式的變化支援 32 位元或 64 位元時間類型，以及 32 位元或 64 位元檔案大小。 第一個數值尾碼 (`32` 或 `64`) 表示時間類型的大小；第二個尾碼為 `i32` 或 `i64`，並且表示檔案大小是以 32 位元還是 64 位元整數表示。 如需支援 32 位元和 64 位元時間類型與檔案大小之版本的資訊，請參閱下表。 如果 `i32` 或 `i64` 尾碼與時間類型的大小相同，則會予以省略，因此 `_findfirst64` 也支援 64 位元檔案長度，而 `_findfirst32` 僅支援 32 位元檔案長度。  
  
 這些函式針對 `fileinfo` 參數使用各種形式的 `_finddata_t` 結構。 如需結構的詳細資訊，請參閱[檔案名稱搜尋函式](../../c-runtime-library/filename-search-functions.md)。  
  
 使用 64 位元時間類型的變化可將檔案建立日期最高表示為 3000 年 12 月 31 日 23:59:59 UTC。 使用 32 位元時間類型的變化僅代表到 2038 年 1 月 18 日 23:59:59 UTC 的日期。 1970 年 1 月 1 日午夜是所有這些函式的日期範圍下限。  
  
 除非您有特定原因要使用明確指定時間大小的版本，否則請使用 `_findfirst` 或 `_wfindfirst`，或者，如果您需要支援大於 3 GB 的檔案大小，請使用 `_findfirsti64` 或 `_wfindfirsti64`。 所有這些函式都使用 64 位元時間類型。 在舊版本中，這些函式都是使用 32 位元時間類型。 如果這是應用程式的重大變更，您可以定義 `_USE_32BIT_TIME_T` 來還原成舊行為。 如果定義 `_USE_32BIT_TIME_T`，`_findfirst`、`_finfirsti64` 和其對應的 Unicode 版本會使用 32 位元時間。  
  
### <a name="time-type-and-file-length-type-variations-of-findfirst"></a>_findfirst 的時間類型和檔案長度類型變化  
  
|函式|已定義 `_USE_32BIT_TIME_T` 嗎？|時間類型|檔案長度類型|  
|---------------|----------------------------------|---------------|----------------------|  
|`_findfirst`, `_wfindfirst`|未定義|64 位元|32 位元|  
|`_findfirst`, `_wfindfirst`|已定義|32 位元|32 位元|  
|`_findfirst32`, `_wfindfirst32`|不會受到巨集定義的影響|32 位元|32 位元|  
|`_findfirst64`, `_wfindfirst64`|不會受到巨集定義的影響|64 位元|64 位元|  
|`_findfirsti64`, `_wfindfirsti64`|未定義|64 位元|64 位元|  
|`_findfirsti64`, `_wfindfirsti64`|已定義|32 位元|64 位元|  
|`_findfirst32i64`, `_wfindfirst32i64`|不會受到巨集定義的影響|32 位元|64 位元|  
|`_findfirst64i32`, `_wfindfirst64i32`|不會受到巨集定義的影響|64 位元|32 位元|  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tfindfirst`|`_findfirst`|`_findfirst`|`_wfindfirst`|  
|`_tfindfirst32`|`_findfirst32`|`_findfirst32`|`_wfindfirst32`|  
|`_tfindfirst64`|`_findfirst64`|`_findfirst64`|`_wfindfirst64`|  
|`_tfindfirsti64`|`_findfirsti64`|`_findfirsti64`|`_wfindfirsti64`|  
|`_tfindfirst32i64`|`_findfirst32i64`|`_findfirst32i64`|`_wfindfirst32i64`|  
|`_tfindfirst64i32`|`_findfirst64i32`|`_findfirst64i32`|`_wfindfirst64i32`|  
  
## <a name="requirements"></a>需求  
  
|函式|必要的標頭|  
|--------------|---------------------|  
|`_findfirst`|\<io.h>|  
|`_findfirst32`|\<io.h>|  
|`_findfirst64`|\<io.h>|  
|`_findfirsti64`|\<io.h>|  
|`_findfirst32i64`|\<io.h>|  
|`_findfirst64i32`|\<io.h>|  
|`_wfindfirst`|\<io.h> 或 \<wchar.h>|  
|`_wfindfirst32`|\<io.h> 或 \<wchar.h>|  
|`_wfindfirst64`|\<io.h> 或 \<wchar.h>|  
|`_wfindfirsti64`|\<io.h> 或 \<wchar.h>|  
|`_wfindfirst32i64`|\<io.h> 或 \<wchar.h>|  
|`_wfindfirst64i32`|\<io.h> 或 \<wchar.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="net-framework-equivalent"></a>.NET Framework 同等  
 [System::IO::DirectoryInfo::GetFiles](https://msdn.microsoft.com/en-us/library/system.io.directoryinfo.getfiles.aspx)  
  
## <a name="see-also"></a>另請參閱  
 [系統呼叫](../../c-runtime-library/system-calls.md)   
 [檔案名稱搜尋函式](../../c-runtime-library/filename-search-functions.md)
