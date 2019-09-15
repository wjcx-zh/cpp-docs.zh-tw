---
title: timespec_get, _timespec32_get, _timespec64_get1
ms.date: 11/04/2016
api_name:
- timespec_get
- _timespec32_get
- _timespec64_get
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- timespec_get
- _timespec32_get
- _timespec64_get
- time/timespec_get
- time/_timespec32_get
- time/_timespec64_get
- timespec
- _timespec32
- _timespec64
helpviewer_keywords:
- timespec_get function
- _timespec32_get function
- _timespec64_get function
ms.assetid: ed757258-b4f2-4c1d-a91b-22ea6ffce4ab
ms.openlocfilehash: c0517c974bf58d502133ccd9868149bd178790d6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957624"
---
# <a name="timespec_get-_timespec32_get-_timespec64_get"></a>timespec_get、_timespec32_get、_timespec64_get

使用第一個引數，依據指定的時間基礎，將間隔設定成指向目前的月曆時間。

## <a name="syntax"></a>語法

```C
int timespec_get(
    struct timespec* const time_spec,
    int const base
);
int _timespec32_get(
    struct _timespec32* const time_spec,
    int const base
);
int _timespec64_get(
    struct _timespec64* const time_spec,
    int const base
);
```

### <a name="parameters"></a>參數

*time_spec*<br/>
設定為自 Epoch 啟動後所經歷之時間 (以秒及奈秒為單位) 的結構指標。

*base*<br/>
非零實作的專用值，會指定時間依據。

## <a name="return-value"></a>傳回值

如果成功，則為*base*的值，否則會傳回零。

## <a name="remarks"></a>備註

**Timespec_get**函數會在*time_spec*引數所指向的結構中設定目前的時間。 此結構的所有版本都有兩個成員： **tv_sec**和**tv_nsec**。 **Tv_sec**值會設定為整數秒數，而**tv_nsec**為整數個毫數，從*基底*指定的 epoch 開始，舍入到系統時鐘的解析。

**Microsoft 專屬**

這些函數只支援**TIME_UTC**作為*基底*值。 這會將*time_spec*值設定為自 epoch 啟動之後的秒數和毫微秒數（以1970年1月1日午夜，國際標準時間（UTC）為單位）。 在**結構** **_timespec32**中， **tv_sec**是 **__time32_t**值。 在**結構** **_timespec64**中， **tv_sec**是 **__time64_t**值。 在**結構** **timespec**中， **tv_sec**是**time_t**型別，其長度為32位或64位，視預處理器宏 _USE_32BIT_TIME_T 是否已定義而定。 **Timespec_get**函式是內嵌函數，會在定義 _USE_32BIT_TIME_T 時呼叫 **_timespec32_get** ;否則，它會呼叫 **_timespec64_get**。

**結束 Microsoft 專有**

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**timespec_get**、 **_timespec32_get**、 **_timespec64_get**|C: \<time.h>，C++： \<ctime> 或 \<time.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[時間管理](../../c-runtime-library/time-management.md)<br/>
[asctime、_wasctime](asctime-wasctime.md)<br/>
[asctime_s、_wasctime_s](asctime-s-wasctime-s.md)<br/>
[_ftime、_ftime32、_ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime、_gmtime32、_gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[gmtime_s、_gmtime32_s、_gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime、_localtime32、_localtime64](localtime-localtime32-localtime64.md)<br/>
[localtime_s、_localtime32_s、_localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
[_utime、_utime32、_utime64、_wutime、_wutime32、_wutime64](utime-utime32-utime64-wutime-wutime32-wutime64.md)<br/>
