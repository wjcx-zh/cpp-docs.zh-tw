---
title: "_findnext、_findnext32、_findnext32i64、_findnext64、_findnext64i32、_findnexti64、_wfindnext、_wfindnext32、_wfindnext32i64、_wfindnext64、_wfindnext64i32、_wfindnexti64 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wfindnext
- _findnext
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
- findnext
- _wfindnext32i64
- _tfindnext64i32
- findnext32
- findnext32i64
- wfindnext64i32
- _wfindnext
- tfindnext64
- findnexti64
- _findnexti64
- _tfindnexti64
- _findnext64i32
- tfindnexti64
- tfindnext32
- _wfindnext64i32
- findnext64i32
- _findnext
- _tfindnext32i64
- _wfindnext64
- wfindnext
- wfindnext32
- tfindnext32i64
- _findnext64
- _tfindnext64
- _wfindnext32
- findnext64
- _findnext32i64
- tfindnext
- wfindnexti64
- tfindnext64i32
- _tfindnext32
- wfindnext32i64
- wfindnext64
- _wfindnexti64
- _tfindnext
- _findnext32
dev_langs: C++
helpviewer_keywords:
- _wfindnexti64 function
- _tfindnext32 function
- wfindnexti64 function
- _wfindnext32i64 function
- findnext32i64 function
- tfindnext64i32 function
- _tfindnext64i32 function
- _findnext function
- findnext64i32 function
- _tfindnext function
- findnext32 function
- tfindnext32 function
- _findnext32 function
- _tfindnext32i64 function
- _wfindnext function
- tfindnext function
- _findnext64 function
- findnext64 function
- _findnext64i32 function
- wfindnext32i64 function
- findnext function
- wfindnext32 function
- _wfindnext64i32 function
- findnexti64 function
- _wfindnext64 function
- _findnext32i64 function
- _findnexti64 function
- _tfindnext64 function
- wfindnext64i32 function
- tfindnexti64 function
- wfindnext64 function
- wfindnext function
- tfindnext64 function
- _wfindnext32 function
- tfindnext32i64 function
- _tfindnexti64 function
ms.assetid: 75d97188-5add-4698-a46c-4c492378f0f8
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6fbb76781c04afb1de970cde3d233d54909b64a6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="findnext-findnext32-findnext32i64-findnext64-findnext64i32-findnexti64-wfindnext-wfindnext32-wfindnext32i64-wfindnext64-wfindnext64i32-wfindnexti64"></a>_findnext、_findnext32、_findnext32i64、_findnext64、_findnext64i32、_findnexti64、_wfindnext、_wfindnext32、_wfindnext32i64、_wfindnext64、_wfindnext64i32、_wfindnexti64
尋找符合前一個 [_findfirst](../../c-runtime-library/reference/findfirst-functions.md) 呼叫中之 `filespec` 引數的下一個名稱 (如果有的話)，然後據此變更 `fileinfo` 結構內容。  
  
## <a name="syntax"></a>語法  
  
```  
int _findnext(  
   intptr_t handle,  
   struct _finddata_t *fileinfo   
);  
int _findnext32(  
   intptr_t handle,  
   struct _finddata32_t *fileinfo   
);  
int _findnext64(  
   intptr_t handle,  
   struct __finddata64_t *fileinfo   
);  
int _findnexti64(  
   intptr_t handle,  
   struct __finddatai64_t *fileinfo   
);  
int _findnext32i64(  
   intptr_t handle,  
   struct _finddata32i64_t *fileinfo   
);  
int _findnext64i32(  
   intptr_t handle,  
   struct _finddata64i32_t *fileinfo   
);  
int _wfindnext(  
   intptr_t handle,  
   struct _wfinddata_t *fileinfo   
);  
int _wfindnext32(  
   intptr_t handle,  
   struct _wfinddata32_t *fileinfo   
);  
int _wfindnext64(  
   intptr_t handle,  
   struct _wfinddata64_t *fileinfo   
);  
int _wfindnexti64(  
   intptr_t handle,  
   struct _wfinddatai64_t *fileinfo   
);  
int _wfindnext32i64(  
   intptr_t handle,  
   struct _wfinddatai64_t *fileinfo   
);  
int _wfindnext64i32(  
   intptr_t handle,  
   struct _wfinddata64i32_t *fileinfo   
);  
```  
  
#### <a name="parameters"></a>參數  
 `handle`  
 搜尋先前 `_findfirst` 呼叫所傳回的控制代碼。  
  
 `fileinfo`  
 檔案資訊緩衝區。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 0。 否則，傳回-1，並設定`errno`為值，表示失敗的性質。 下表顯示可能的錯誤碼。  
  
 `EINVAL`  
 參數無效：`fileinfo` 是 `NULL`。 或者，作業系統傳回未預期的錯誤。  
  
 `ENOENT`  
 無法再找到相符檔案。  
  
 `ENOMEM`  
 記憶體不足，或檔名的長度超過 `MAX_PATH`。  
  
 如果傳入無效參數，則這些函式會叫用無效的參數處理常式 (如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述)。  
  
## <a name="remarks"></a>備註  
 在您完成使用 `_findfirst` 或 `_findnext` 函式 (或任何變體) 之後，必須呼叫 [_findclose](../../c-runtime-library/reference/findclose.md)。 這會釋放應用程式中這些函式所使用的資源。  
  
 具有 `w` 前置詞的這些函式變化是寬字元版本；否則，它們與對應的單一位元組函式相同。  
  
 這些函式的變化支援 32 位元或 64 位元時間類型，以及 32 位元或 64 位元檔案大小。 第一個數值後置字元 (`32` 或 `64`) 表示所使用的時間類型大小，第二個後置字元為 `i32` 或 `i64`，表示檔案大小是以 32 位元或 64 位元整數來表示。 如需支援 32 位元和 64 位元時間類型與檔案大小之版本的資訊，請參閱下表。 使用 64 位元時間類型的變化可將檔案建立日期最高表示為 3000 年 12 月 31 日 23:59:59 UTC；而使用 32 位元時間類型的變化僅代表到 2038 年 1 月 18 日 23:59:59 UTC 的日期。 1970 年 1 月 1 日午夜是所有這些函式的日期範圍下限。  
  
 除非您有特定原因要使用明確指定時間大小的版本，否則請使用 `_findnext` 或 `_wfindnext`或者，如果您需要支援大於 3 GB 的檔案大小，請使用 `_findnexti64` 或 `_wfindnexti64`。 所有這些函式都使用 64 位元時間類型。 在舊版本中，這些函式都是使用 32 位元時間類型。 如果這是應用程式的重大變更，您可以定義 `_USE_32BIT_TIME_T` 來取得舊行為。 如果定義 `_USE_32BIT_TIME_T`，`_findnext`、`_finnexti64` 和其對應的 Unicode 版本會使用 32 位元時間。  
  
### <a name="time-type-and-file-length-type-variations-of-findnext"></a>_findnext 的時間類型和檔案長度類型變化  
  
|函式|已定義 `_USE_32BIT_TIME_T` 嗎？|時間類型|檔案長度類型|  
|---------------|----------------------------------|---------------|----------------------|  
|`_findnext`, `_wfindnext`|未定義|64 位元|32 位元|  
|`_findnext`, `_wfindnext`|已定義|32 位元|32 位元|  
|`_findnext32`, `_wfindnext32`|不會受到巨集定義的影響|32 位元|32 位元|  
|`_findnext64`, `_wfindnext64`|不會受到巨集定義的影響|64 位元|64 位元|  
|`_findnexti64`, `_wfindnexti64`|未定義|64 位元|64 位元|  
|`_findnexti64`, `_wfindnexti64`|已定義|32 位元|64 位元|  
|`_findnext32i64`, `_wfindnext32i64`|不會受到巨集定義的影響|32 位元|64 位元|  
|`_findnext64i32`, `_wfindnext64i32`|不會受到巨集定義的影響|64 位元|32 位元|  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tfindnext`|`_findnext`|`_findnext`|`_wfindnext`|  
|`_tfindnext32`|`_findnext32`|`_findnext32`|`_wfindnext32`|  
|`_tfindnext64`|`_findnext64`|`_findnext64`|`_wfindnext64`|  
|`_tfindnexti64`|`_findnexti64`|`_findnexti64`|`_wfindnexti64`|  
|`_tfindnext32i64`|`_findnext32i64`|`_findnext32i64`|`_wfindnext32i64`|  
|`_tfindnext64i32`|`_findnext64i32`|`_findnext64i32`|`_wfindnext64i32`|  
  
## <a name="requirements"></a>需求  
  
|功能|必要的標頭|  
|--------------|---------------------|  
|`_findnext`|\<io.h>|  
|`_findnext32`|\<io.h>|  
|`_findnext64`|\<io.h>|  
|`_findnexti64`|\<io.h>|  
|`_findnext32i64`|\<io.h>|  
|`_findnext64i32`|\<io.h>|  
|`_wfindnext`|\<io.h> 或 \<wchar.h>|  
|`_wfindnext32`|\<io.h> 或 \<wchar.h>|  
|`_wfindnext64`|\<io.h> 或 \<wchar.h>|  
|`_wfindnexti64`|\<io.h> 或 \<wchar.h>|  
|`_wfindnext32i64`|\<io.h> 或 \<wchar.h>|  
|`_wfindnext64i32`|\<io.h> 或 \<wchar.h>|  
  
 如需相容性詳細資訊，請參閱簡介中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="libraries"></a>程式庫  
 所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="see-also"></a>請參閱  
 [系統呼叫](../../c-runtime-library/system-calls.md)   
 [檔案名稱搜尋函式](../../c-runtime-library/filename-search-functions.md)