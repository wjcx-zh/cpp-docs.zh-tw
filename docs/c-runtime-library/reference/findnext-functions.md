---
title: _findnext、_findnext32、_findnext32i64、_findnext64、_findnext64i32、_findnexti64、_wfindnext、_wfindnext32、_wfindnext32i64、_wfindnext64、_wfindnext64i32、_wfindnexti64
ms.date: 4/2/2020
api_name:
- _findnext
- _findnext32
- _findnext32i64
- _findnext64
- _findnext64i32
- _findnexti64
- _wfindnext
- _wfindnext32
- _wfindnext32i64
- _wfindnext64
- _wfindnext64i32
- _wfindnexti64
- _o__findnext32
- _o__findnext32i64
- _o__findnext64
- _o__findnext64i32
- _o__wfindnext32
- _o__wfindnext32i64
- _o__wfindnext64
- _o__wfindnext64i32
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: acb680db3b07b0f600b758401f1270deccf03da7
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82911656"
---
# <a name="_findnext-_findnext32-_findnext32i64-_findnext64-_findnext64i32-_findnexti64-_wfindnext-_wfindnext32-_wfindnext32i64-_wfindnext64-_wfindnext64i32-_wfindnexti64"></a>_findnext、_findnext32、_findnext32i64、_findnext64、_findnext64i32、_findnexti64、_wfindnext、_wfindnext32、_wfindnext32i64、_wfindnext64、_wfindnext64i32、_wfindnexti64

找出符合先前[_findfirst](findfirst-functions.md)呼叫中*filespec*引數的下一個名稱（如果有的話），然後據以變更*fileinfo*結構內容。

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

*圖*<br/>
先前的呼叫所傳回的搜尋控制碼 **_findfirst**。

*fileinfo*<br/>
檔案資訊緩衝區。

## <a name="return-value"></a>傳回值

如果成功，會傳回 0。 否則，會傳回-1，並將**errno**設定為指出失敗本質的值。 下表顯示可能的錯誤碼。

|errno 值|條件|
|-|-|
| **EINVAL** | 不正確參數： *fileinfo*為**Null**。 或者，作業系統傳回未預期的錯誤。 |
| **ENOENT** | 無法再找到相符檔案。 |
| **ENOMEM** | 記憶體不足或檔案名稱的長度超過**MAX_PATH**。 |

如果傳入無效參數，則這些函式會叫用無效的參數處理常式 (如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述)。

## <a name="remarks"></a>備註

當您使用完 **_findfirst**或 **_findnext**函式（或任何變體）之後，必須呼叫[_findclose](findclose.md) 。 這會釋放應用程式中這些函式所使用的資源。

使用**w**前置詞的這些函式的變化是寬字元版本;否則，它們與對應的單一位元組函式相同。

這些函式的變化支援 32 位元或 64 位元時間類型，以及 32 位元或 64 位元檔案大小。 第一個數位尾碼（**32**或**64**）表示所使用的時間類型大小;第二個尾碼為**i32**或**i64**，指出檔案大小是否以32位或64位整數表示。 如需支援 32 位元和 64 位元時間類型與檔案大小之版本的資訊，請參閱下表。 使用 64 位元時間類型的變化可將檔案建立日期最高表示為 3000 年 12 月 31 日 23:59:59 UTC；而使用 32 位元時間類型的變化僅代表到 2038 年 1 月 18 日 23:59:59 UTC 的日期。 1970 年 1 月 1 日午夜是所有這些函式的日期範圍下限。

除非您有特定原因要使用明確指定時間大小的版本，否則請使用 **_findnext**或 **_wfindnext**或者，如果您需要支援大於 3 GB 的檔案大小，請使用 **_findnexti64**或 **_wfindnexti64**。 所有這些函式都使用 64 位元時間類型。 在舊版本中，這些函式都是使用 32 位元時間類型。 如果這是應用程式的重大變更，您可以定義 **_USE_32BIT_TIME_T**來取得舊的行為。 如果 **_USE_32BIT_TIME_T**已定義， **_findnext**、 **_Finnexti64**和其對應的 Unicode 版本會使用32位的時間。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="time-type-and-file-length-type-variations-of-_findnext"></a>_findnext 的時間類型和檔案長度類型變化

|函式|**_USE_32BIT_TIME_T**定義了嗎？|時間類型|檔案長度類型|
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

|函式|必要的標頭|
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

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[系統呼叫](../../c-runtime-library/system-calls.md)<br/>
[檔案名稱搜尋函式](../../c-runtime-library/filename-search-functions.md)<br/>
