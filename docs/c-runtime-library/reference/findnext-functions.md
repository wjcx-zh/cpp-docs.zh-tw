---
title: _findnext、_findnext32、_findnext32i64、_findnext64、_findnext64i32、_findnexti64、_wfindnext、_wfindnext32、_wfindnext32i64、_wfindnext64、_wfindnext64i32、_wfindnexti64 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 540ec2aae5e13df68438c74e0371e91326e9bb0a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="findnext-findnext32-findnext32i64-findnext64-findnext64i32-findnexti64-wfindnext-wfindnext32-wfindnext32i64-wfindnext64-wfindnext64i32-wfindnexti64"></a>_findnext、_findnext32、_findnext32i64、_findnext64、_findnext64i32、_findnexti64、_wfindnext、_wfindnext32、_wfindnext32i64、_wfindnext64、_wfindnext64i32、_wfindnexti64

尋找下一個的名稱，如果有符合*filespec*先前呼叫中的引數[_findfirst](findfirst-functions.md)，然後再修改*fileinfo*據此結構內容。

## <a name="syntax"></a>語法

```C
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

### <a name="parameters"></a>參數

*控制代碼*<br/>
先前呼叫所傳回的搜尋控制代碼 **_findfirst**。

*fileinfo*<br/>
檔案資訊緩衝區。

## <a name="return-value"></a>傳回值

如果成功，則傳回 0。 否則，傳回-1，並設定**errno**為值，表示失敗的性質。 下表顯示可能的錯誤碼。

|errno 值|條件|
|-|-|
**EINVAL**|無效的參數： *fileinfo*已**NULL**。 或者，作業系統傳回未預期的錯誤。
**ENOENT**|無法再找到相符檔案。
**ENOMEM**|沒有足夠的記憶體或檔案名稱的長度超過**MAX_PATH**。

如果傳入無效參數，則這些函式會叫用無效的參數處理常式 (如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述)。

## <a name="remarks"></a>備註

您必須呼叫[_findclose](findclose.md)使用完畢之後 **_findfirst**或 **_findnext**函式 （或任何變化）。 這會釋放應用程式中這些函式所使用的資源。

這些函式的變化**w**前置詞是寬字元版本，否則它們是對應的單一位元組函式完全相同。

這些函式的變化支援 32 位元或 64 位元時間類型，以及 32 位元或 64 位元檔案大小。 第一個數字尾碼 (**32**或**64**) 表示時間的大小類型使用; 第二個後置詞是**i32**或**i64**，表示檔案大小以 32 位元或 64 位元整數。 如需支援 32 位元和 64 位元時間類型與檔案大小之版本的資訊，請參閱下表。 使用 64 位元時間類型的變化可將檔案建立日期最高表示為 3000 年 12 月 31 日 23:59:59 UTC；而使用 32 位元時間類型的變化僅代表到 2038 年 1 月 18 日 23:59:59 UTC 的日期。 1970 年 1 月 1 日午夜是所有這些函式的日期範圍下限。

除非您有特定的理由来使用的版本，明確地指定時間大小，請使用 **_findnext**或 **_wfindnext**或者，如果您要支援大於 3 GB 的檔案大小，請使用 **_findnexti64**或 **_wfindnexti64**。 所有這些函式都使用 64 位元時間類型。 在舊版本中，這些函式都是使用 32 位元時間類型。 如果這是應用程式的重大變更，您可以定義 **_USE_32BIT_TIME_T**取得舊的行為。 如果 **_USE_32BIT_TIME_T**定義， **_findnext**， **_finnexti64**和其相對應的 Unicode 版本使用 32 位元時間。

### <a name="time-type-and-file-length-type-variations-of-findnext"></a>_findnext 的時間類型和檔案長度類型變化

|函式|**_USE_32BIT_TIME_T**定義嗎？|時間類型|檔案長度類型|
|---------------|----------------------------------|---------------|----------------------|
|**_findnext**， **_wfindnext**|未定義|64 位元|32 位元|
|**_findnext**， **_wfindnext**|已定義|32 位元|32 位元|
|**_findnext32**， **_wfindnext32**|不會受到巨集定義的影響|32 位元|32 位元|
|**_findnext64**， **_wfindnext64**|不會受到巨集定義的影響|64 位元|64 位元|
|**_findnexti64**， **_wfindnexti64**|未定義|64 位元|64 位元|
|**_findnexti64**， **_wfindnexti64**|已定義|32 位元|64 位元|
|**_findnext32i64**， **_wfindnext32i64**|不會受到巨集定義的影響|32 位元|64 位元|
|**_findnext64i32**， **_wfindnext64i32**|不會受到巨集定義的影響|64 位元|32 位元|

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfindnext**|**_findnext**|**_findnext**|**_wfindnext**|
|**_tfindnext32**|**_findnext32**|**_findnext32**|**_wfindnext32**|
|**_tfindnext64**|**_findnext64**|**_findnext64**|**_wfindnext64**|
|**_tfindnexti64**|**_findnexti64**|**_findnexti64**|**_wfindnexti64**|
|**_tfindnext32i64**|**_findnext32i64**|**_findnext32i64**|**_wfindnext32i64**|
|**_tfindnext64i32**|**_findnext64i32**|**_findnext64i32**|**_wfindnext64i32**|

## <a name="requirements"></a>需求

|功能|必要的標頭|
|--------------|---------------------|
|**_findnext**|\<io.h>|
|**_findnext32**|\<io.h>|
|**_findnext64**|\<io.h>|
|**_findnexti64**|\<io.h>|
|**_findnext32i64**|\<io.h>|
|**_findnext64i32**|\<io.h>|
|**_wfindnext**|\<io.h> 或 \<wchar.h>|
|**_wfindnext32**|\<io.h> 或 \<wchar.h>|
|**_wfindnext64**|\<io.h> 或 \<wchar.h>|
|**_wfindnexti64**|\<io.h> 或 \<wchar.h>|
|**_wfindnext32i64**|\<io.h> 或 \<wchar.h>|
|**_wfindnext64i32**|\<io.h> 或 \<wchar.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[系統呼叫](../../c-runtime-library/system-calls.md)<br/>
[檔案名稱搜尋函式](../../c-runtime-library/filename-search-functions.md)<br/>
