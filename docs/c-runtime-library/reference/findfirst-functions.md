---
title: _findfirst、_findfirst32、_findfirst32i64、_findfirst64、_findfirst64i32、_findfirsti64、_wfindfirst、_wfindfirst32、_wfindfirst32i64、_wfindfirst64、_wfindfirst64i32、_wfindfirsti64
ms.date: 4/2/2020
api_name:
- _findfirst
- _wfindfirst
- _findfirst32
- _wfindfirst32
- _findfirst32i64
- _wfindfirst32i64
- _findfirst64
- _wfindfirst64
- _findfirst64i32
- _wfindfirst64i32
- _findfirsti64
- _wfindfirsti64
- _o__findfirst32
- _o__findfirst32i64
- _o__findfirst64
- _o__findfirst64i32
- _o__wfindfirst32
- _o__wfindfirst32i64
- _o__wfindfirst64
- _o__wfindfirst64i32
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
- api-ms-win-crt-filesystem-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: d83cc0913584618897cbc4aec45cb137388674b7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346817"
---
# <a name="_findfirst-_findfirst32-_findfirst32i64-_findfirst64-_findfirst64i32-_findfirsti64-_wfindfirst-_wfindfirst32-_wfindfirst32i64-_wfindfirst64-_wfindfirst64i32-_wfindfirsti64"></a>_findfirst、_findfirst32、_findfirst32i64、_findfirst64、_findfirst64i32、_findfirsti64、_wfindfirst、_wfindfirst32、_wfindfirst32i64、_wfindfirst64、_wfindfirst64i32、_wfindfirsti64

提供有關與*filespec*參數中指定的檔名匹配的檔名的第一個實例的資訊。

## <a name="syntax"></a>語法

```C
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

### <a name="parameters"></a>參數

*檔案規格*<br/>
目標檔案規格 (可以包含萬用字元)。

*檔案資訊*<br/>
檔案資訊緩衝區。

## <a name="return-value"></a>傳回值

如果成功 **,_findfirst**傳回唯一的搜尋句柄,標識與*filespec*規範符合的檔案或檔組,可用於後續呼叫[_findnext](findnext-functions.md)或[_findclose](findclose.md)。 否則 **,_findfirst**返回 -1 並將**errno**設置到以下值之一。

| errno 值 | 條件 |
|-|-|
| **埃因瓦爾** | 不合法參數:*檔案規格*或*檔案資訊*為**NULL**。 或者，作業系統傳回未預期的錯誤。 |
| **埃諾恩特** | 不相符的檔案規格。 |
| **ENOMEM** | 記憶體不足。 |
| **埃因瓦爾** | 不合法的檔案名規範或給定的檔案名大於**MAX_PATH**。 |

如需這些傳回碼和其他傳回碼的資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

如果傳入無效參數，則這些函式會叫用無效的參數處理常式 (如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述)。

## <a name="remarks"></a>備註

完成 **_findfirst**或[_findnext](findnext-functions.md)函數(或任何變體)後,必須調用[_findclose。](findclose.md) 這會釋放應用程式中這些函式所使用的資源。

具有**w**首碼的這些函數的變數是寬字元版本;否則,它們與相應的單位元組函數相同。

這些函式的變化支援 32 位元或 64 位元時間類型，以及 32 位元或 64 位元檔案大小。 第一個數字後綴 (**32**或**64**) 表示時間類型的大小;第二個後綴是**i32**或**i64,** 並指示檔大小是表示為 32 位元還是 64 位整數。 如需支援 32 位元和 64 位元時間類型與檔案大小之版本的資訊，請參閱下表。 如果**i32**或 i64 後綴與時間類型的大小相同,則省略 i32 或**i64**後綴,因此 **_findfirst64**也支援 64 位元檔長度,**並且_findfirst32**僅支援 32 位元檔長度。

這些函數使用各種形式的 **_finddata_t**結構來進行*fileinfo*參數。 如需結構的詳細資訊，請參閱[檔案名稱搜尋函式](../../c-runtime-library/filename-search-functions.md)。

使用 64 位元時間類型的變化可將檔案建立日期最高表示為 3000 年 12 月 31 日 23:59:59 UTC。 使用 32 位元時間類型的變化僅代表到 2038 年 1 月 18 日 23:59:59 UTC 的日期。 1970 年 1 月 1 日午夜是所有這些函式的日期範圍下限。

除非您有特定原因使用顯示式指定時間大小的版本,否則請使用 **_findfirst**或 **_wfindfirst,** 或者,如果需要支援大於 3 GB 的檔案大小,請使用 **_findfirsti64**或 **_wfindfirsti64**。 所有這些函式都使用 64 位元時間類型。 在舊版本中，這些函式都是使用 32 位元時間類型。 如果這是應用程式的重大更改,則可以定義 **_USE_32BIT_TIME_T**以還原到舊行為。 如果定義了 **_USE_32BIT_TIME_T,****則_findfirst** **,_finfirsti64**及其相應的 Unicode 版本使用 32 位時間。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="time-type-and-file-length-type-variations-of-_findfirst"></a>_findfirst 的時間類型和檔案長度類型變化

|函式|**定義_USE_32BIT_TIME_T?**|時間類型|檔案長度類型|
|---------------|----------------------------------|---------------|----------------------|
|**_findfirst**, **_wfindfirst**|未定義|64 位元|32 位元|
|**_findfirst**, **_wfindfirst**|已定義|32 位元|32 位元|
|**_findfirst32**, **_wfindfirst32**|不會受到巨集定義的影響|32 位元|32 位元|
|**_findfirst64**, **_wfindfirst64**|不會受到巨集定義的影響|64 位元|64 位元|
|**_findfirsti64**, **_wfindfirsti64**|未定義|64 位元|64 位元|
|**_findfirsti64**, **_wfindfirsti64**|已定義|32 位元|64 位元|
|**_findfirst32i64**, **_wfindfirst32i64**|不會受到巨集定義的影響|32 位元|64 位元|
|**_findfirst64i32**, **_wfindfirst64i32**|不會受到巨集定義的影響|64 位元|32 位元|

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfindfirst**|**_findfirst**|**_findfirst**|**_wfindfirst**|
|**_tfindfirst32**|**_findfirst32**|**_findfirst32**|**_wfindfirst32**|
|**_tfindfirst64**|**_findfirst64**|**_findfirst64**|**_wfindfirst64**|
|**_tfindfirsti64**|**_findfirsti64**|**_findfirsti64**|**_wfindfirsti64**|
|**_tfindfirst32i64**|**_findfirst32i64**|**_findfirst32i64**|**_wfindfirst32i64**|
|**_tfindfirst64i32**|**_findfirst64i32**|**_findfirst64i32**|**_wfindfirst64i32**|

## <a name="requirements"></a>需求

|函式|必要的標頭|
|--------------|---------------------|
|**_findfirst**|\<io.h>|
|**_findfirst32**|\<io.h>|
|**_findfirst64**|\<io.h>|
|**_findfirsti64**|\<io.h>|
|**_findfirst32i64**|\<io.h>|
|**_findfirst64i32**|\<io.h>|
|**_wfindfirst**|\<io.h> 或 \<wchar.h>|
|**_wfindfirst32**|\<io.h> 或 \<wchar.h>|
|**_wfindfirst64**|\<io.h> 或 \<wchar.h>|
|**_wfindfirsti64**|\<io.h> 或 \<wchar.h>|
|**_wfindfirst32i64**|\<io.h> 或 \<wchar.h>|
|**_wfindfirst64i32**|\<io.h> 或 \<wchar.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[系統呼叫](../../c-runtime-library/system-calls.md)<br/>
[檔案名稱搜尋函式](../../c-runtime-library/filename-search-functions.md)<br/>
