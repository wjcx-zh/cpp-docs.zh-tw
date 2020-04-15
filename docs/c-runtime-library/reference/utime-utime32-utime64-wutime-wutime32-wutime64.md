---
title: _utime、_utime32、_utime64、_wutime、_wutime32、_wutime64
ms.date: 4/2/2020
api_name:
- _utime64
- _utime
- _wutime
- _wutime64
- _wutime32
- _utime32
- _o__utime32
- _o__utime64
- _o__wutime32
- _o__wutime64
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
- api-ms-win-crt-time-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tutime
- _utime64
- wutime
- utime32
- wutime64
- _utime
- wutime32
- _wutime
- utime
- utime64
- _wutime64
- _utime32
- _tutime64
- _wutime32
helpviewer_keywords:
- tutime function
- utime32 function
- utime64 function
- _utime function
- _tutime32 function
- time [C++], file modification
- wutime function
- _wutime function
- _wutime32 function
- _tutime64 function
- _tutime function
- files [C++], modification time
- _wutime64 function
- _utime32 function
- utime function
- _utime64 function
- wutime64 function
- wutime32 function
- tutime64 function
- tutime32 function
ms.assetid: 8d482d40-19b9-4591-bfee-5d7f601d1a9e
ms.openlocfilehash: 5c530f46877bdb23fc51fb49beab8abfc0c16b2f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361198"
---
# <a name="_utime-_utime32-_utime64-_wutime-_wutime32-_wutime64"></a>_utime、_utime32、_utime64、_wutime、_wutime32、_wutime64

設定檔案修改時間。

## <a name="syntax"></a>語法

```C
int _utime(
   const char *filename,
   struct _utimbuf *times
);
int _utime32(
   const char *filename,
   struct __utimbuf32 *times
);
int _utime64(
   const char *filename,
   struct __utimbuf64 *times
);
int _wutime(
   const wchar_t *filename,
   struct _utimbuf *times
);
int _wutime32(
   const wchar_t *filename,
   struct __utimbuf32 *times
);
int _wutime64(
   const wchar_t *filename,
   struct __utimbuf64 *times
);
```

### <a name="parameters"></a>參數

*檔案名稱*<br/>
包含路徑或檔名之字串的指標。

*次*<br/>
預存時間值的指標。

## <a name="return-value"></a>傳回值

如果檔案修改時間變更，則所有這些函式都會傳回 0。 返回值 -1 表示錯誤。 如果傳遞無效參數，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,這些函數將返回 **-1,errno**設置為以下值之一:

|errno 值|條件|
|-|-|
| **EACCES** | 路徑指定目錄或唯讀檔案 |
| **埃因瓦爾** | 無效*時間*參數 |
| **EMFILE** | 開啟太多檔案 (必須開啟檔案，才能變更其修改時間) |
| **埃諾恩特** | 找不到路徑或檔名 |

有關這些代碼和其他返回代碼的詳細資訊[,請參閱_doserrno、errno、_sys_errlist和_sys_nerr。](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)

如果變更日期晚於 1970 年 1 月 1 日午夜，且早於所使用函式的結束日期，則可以變更檔案的日期。 **_utime**和 **_wutime**使用 64 位元時間值,因此結束日期為 23:59:59,12 月 31 日,3000,UTC。 如果定義 **_USE_32BIT_TIME_T**以強制舊行為,則結束日期為 2038 年 1 月 18 日 23:59:59,UTC。 **_utime32**或 **_wutime32**使用 32 位元時間類型,無論**是否定義了_USE_32BIT_TIME_T,** 並且始終具有較早的結束日期。 **_utime64**或 **_wutime64**始終使用 64 位元時間類型,因此這些函數始終支援較晚的結束日期。

## <a name="remarks"></a>備註

**_utime**函數設定*檔名*指定的檔的修改時間。 處理序必須具有檔案的寫入權，才能變更時間。 在 Windows 作業系統中,您可以更改 **_utimbuf**結構中的訪問時間和修改時間。 如果*時間*是**NULL**指標,則修改時間設定為目前本地時間。 否則,*時間*必須指向在 SYS_UTIME 中定義的 **_utimbuf**類型的結構。H。

**_utimbuf**結構存儲 **_utime**用於更改檔修改日期的檔案存取和修改時間。 結構具有以下欄位,這些欄位都是**time_t**類型:

| 欄位 |   |
|-------|---|
| **交流時間** | 檔案存取的時間 |
| **模制時間** | 檔案修改的時間 |

**_utimbuf**結構的特定版本 **(_utimebuf32**和 **__utimbuf64**)使用時間類型的 32 位元和 64 位元版本定義。 這些是用在此函式的 32 位元和 64 位元特定版本。 **預設情況下,除非**定義了 **_USE_32BIT_TIME_T,** 否則_utimbuf本身使用 64 位元時間類型。

**_utime**與 **_futime**相同,只是 **_utime***的檔名*參數是檔名或檔的路徑,而不是打開檔案的檔案描述符。

**_wutime**是 **_utime**的寬字元版本;要 **_wutime***的檔案名*參數是寬字元字串。 除此之外，這些函式的行為相同。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tutime**|**_utime**|**_utime**|**_wutime**|
|**_tutime32**|**_utime32**|**_utime32**|**_wutime32**|
|**_tutime64**|**_utime64**|**_utime64**|**_wutime64**|

## <a name="requirements"></a>需求

|常式傳回的值|必要標頭|選擇性標頭|
|-------------|----------------------|----------------------|
|**_utime**, **_utime32**, **_utime64**|\<sys/utime.h>|\<errno.h>|
|**_utime64**|\<sys/utime.h>|\<errno.h>|
|**_wutime**|\<utime.h> 或 \<wchar.h>|\<errno.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

此程式使用 **_utime**將檔案修改時間設定為當前時間。

```C
// crt_utime.c
#include <stdio.h>
#include <stdlib.h>
#include <sys/types.h>
#include <sys/utime.h>
#include <time.h>

int main( void )
{
   struct tm tma = {0}, tmm = {0};
   struct _utimbuf ut;

   // Fill out the accessed time structure
   tma.tm_hour = 12;
   tma.tm_isdst = 0;
   tma.tm_mday = 15;
   tma.tm_min = 0;
   tma.tm_mon = 0;
   tma.tm_sec = 0;
   tma.tm_year = 103;

   // Fill out the modified time structure
   tmm.tm_hour = 12;
   tmm.tm_isdst = 0;
   tmm.tm_mday = 15;
   tmm.tm_min = 0;
   tmm.tm_mon = 0;
   tmm.tm_sec = 0;
   tmm.tm_year = 102;

   // Convert tm to time_t
   ut.actime = mktime(&tma);
   ut.modtime = mktime(&tmm);

   // Show file time before and after
   system( "dir crt_utime.c" );
   if( _utime( "crt_utime.c", &ut ) == -1 )
      perror( "_utime failed\n" );
   else
      printf( "File time modified\n" );
   system( "dir crt_utime.c" );
}
```

### <a name="sample-output"></a>範例輸出

```Output
Volume in drive C has no label.
Volume Serial Number is 9CAC-DE74

Directory of C:\test

01/09/2003  05:38 PM               935 crt_utime.c
               1 File(s)            935 bytes
               0 Dir(s)  20,742,955,008 bytes free
File time modified
Volume in drive C has no label.
Volume Serial Number is 9CAC-DE74

Directory of C:\test

01/15/2002  12:00 PM               935 crt_utime.c
               1 File(s)            935 bytes
               0 Dir(s)  20,742,955,008 bytes free
```

## <a name="see-also"></a>另請參閱

[時間管理](../../c-runtime-library/time-management.md)<br/>
[asctime、_wasctime](asctime-wasctime.md)<br/>
[ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_fstat、_fstat32、_fstat64、_fstati64、_fstat32i64、_fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_ftime、_ftime32、_ftime64](ftime-ftime32-ftime64.md)<br/>
[_futime、_futime32、_futime64](futime-futime32-futime64.md)<br/>
[gmtime、_gmtime32、_gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime、_localtime32、_localtime64](localtime-localtime32-localtime64.md)<br/>
[_stat、_wstat 函式](stat-functions.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
