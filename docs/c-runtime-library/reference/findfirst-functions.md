---
title: _findfirst、_findfirst32、_findfirst32i64、_findfirst64、_findfirst64i32、_findfirsti64、_wfindfirst、_wfindfirst32、_wfindfirst32i64、_wfindfirst64、_wfindfirst64i32、_wfindfirsti64 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
ms.workload:
- cplusplus
ms.openlocfilehash: ff0827420392744d0cc362b02f87ad093b7ce950
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="findfirst-findfirst32-findfirst32i64-findfirst64-findfirst64i32-findfirsti64-wfindfirst-wfindfirst32-wfindfirst32i64-wfindfirst64-wfindfirst64i32-wfindfirsti64"></a>_findfirst、_findfirst32、_findfirst32i64、_findfirst64、_findfirst64i32、_findfirsti64、_wfindfirst、_wfindfirst32、_wfindfirst32i64、_wfindfirst64、_wfindfirst64i32、_wfindfirsti64

提供的檔名指定的檔案相符，第一個執行個體的相關資訊*filespec*引數。

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

*fileinfo*<br/>
檔案資訊緩衝區。

## <a name="return-value"></a>傳回值

如果成功的話， **_findfirst**識別符合的檔案群組的檔案將唯一的搜尋控制代碼傳回*filespec*規格，可用於後續呼叫[_findnext](findnext-functions.md)或[_findclose](findclose.md)。 否則， **_findfirst**傳回-1，並設定**errno**至下列值之一。

|errno 值|條件|
|-|-|
**EINVAL**|無效的參數： *filespec*或*fileinfo*已**NULL**。 或者，作業系統傳回未預期的錯誤。
**ENOENT**|不相符的檔案規格。
**ENOMEM**|記憶體不足。
**EINVAL**|無效的檔案名稱的規格或指定的檔案名稱超過**MAX_PATH**。

如需有關這些傳回碼和其他傳回碼的詳細資訊，請參閱 [_doserrno, errno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

如果傳入無效參數，則這些函式會叫用無效的參數處理常式 (如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述)。

## <a name="remarks"></a>備註

您必須呼叫[_findclose](findclose.md)您完成其中一種之後 **_findfirst**或[_findnext](findnext-functions.md)函式 （或任何變化）。 這會釋放應用程式中這些函式所使用的資源。

有這些函式的變化**w**前置詞是寬字元版本，否則它們是對應的單一位元組函式完全相同。

這些函式的變化支援 32 位元或 64 位元時間類型，以及 32 位元或 64 位元檔案大小。 第一個數值後置詞 (**32**或**64**) 表示的時間類型大小; 第二個後置詞是**i32**或**i64**，並指出是否檔案大小被以 32 位元或 64 位元整數。 如需支援 32 位元和 64 位元時間類型與檔案大小之版本的資訊，請參閱下表。 **I32**或**i64**如果因此是時間類型的大小相同，則會忽略尾碼 **_findfirst64**也支援 64 位元檔案長度和 **_findfirst32**支援僅 32 位元檔案長度。

這些函式會使用各種形式的 **_finddata_t**結構*fileinfo*參數。 如需結構的詳細資訊，請參閱[檔案名稱搜尋函式](../../c-runtime-library/filename-search-functions.md)。

使用 64 位元時間類型的變化可將檔案建立日期最高表示為 3000 年 12 月 31 日 23:59:59 UTC。 使用 32 位元時間類型的變化僅代表到 2038 年 1 月 18 日 23:59:59 UTC 的日期。 1970 年 1 月 1 日午夜是所有這些函式的日期範圍下限。

除非您有特定的理由来使用的版本，明確地指定時間大小，請使用 **_findfirst**或 **_wfindfirst**或者，如果您要支援超過 3 GB 的檔案大小，請使用 **_findfirsti64**或 **_wfindfirsti64**。 所有這些函式都使用 64 位元時間類型。 在舊版本中，這些函式都是使用 32 位元時間類型。 如果這是應用程式的重大變更，您可以定義 **_USE_32BIT_TIME_T**還原舊版的行為。 如果 **_USE_32BIT_TIME_T**定義， **_findfirst**， **_finfirsti64**，和其相對應的 Unicode 版本使用 32 位元時間。

### <a name="time-type-and-file-length-type-variations-of-findfirst"></a>_findfirst 的時間類型和檔案長度類型變化

|函式|**_USE_32BIT_TIME_T**定義嗎？|時間類型|檔案長度類型|
|---------------|----------------------------------|---------------|----------------------|
|**_findfirst**， **_wfindfirst**|未定義|64 位元|32 位元|
|**_findfirst**， **_wfindfirst**|已定義|32 位元|32 位元|
|**_findfirst32**， **_wfindfirst32**|不會受到巨集定義的影響|32 位元|32 位元|
|**_findfirst64**， **_wfindfirst64**|不會受到巨集定義的影響|64 位元|64 位元|
|**_findfirsti64**， **_wfindfirsti64**|未定義|64 位元|64 位元|
|**_findfirsti64**， **_wfindfirsti64**|已定義|32 位元|64 位元|
|**_findfirst32i64**， **_wfindfirst32i64**|不會受到巨集定義的影響|32 位元|64 位元|
|**_findfirst64i32**， **_wfindfirst64i32**|不會受到巨集定義的影響|64 位元|32 位元|

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

|功能|必要的標頭|
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

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[系統呼叫](../../c-runtime-library/system-calls.md)<br/>
[檔案名稱搜尋函式](../../c-runtime-library/filename-search-functions.md)<br/>
