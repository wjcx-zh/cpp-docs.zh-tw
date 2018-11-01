---
title: timespec_get _timespec32_get _timespec64_get1
ms.date: 11/04/2016
apiname:
- timespec_get
- _timespec32_get
- _timespec64_get
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
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: c1d0cbaf194060d816e31d397a9319ef47f75371
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50638447"
---
# <a name="timespecget-timespec32get-timespec64get"></a>timespec_get、_timespec32_get、_timespec64_get

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

值*基底*如果成功，否則會傳回零。

## <a name="remarks"></a>備註

**Timespec_get**函式中所指向的結構會將目前的時間*time_spec*引數。 所有版本的此結構都具有兩個成員， **tv_sec**並**tv_nsec**。 **Tv_sec**值設定為整數秒數和**tv_nsec**奈秒的整數的數字，四捨五入到系統時鐘的解析度所指定的epoch啟動之後*基底*。

**Microsoft 專屬**

這些函式僅支援**TIME_UTC**作為*基底*值。 這會設定*time_spec*秒及奈自 epoch 啟動，1970 年 1 月 1 日午夜 Coordinated Universal Time (UTC) 之後的數字的值。 在  **struct** **_timespec32**， **tv_sec**是 **__time32_t**值。 在  **struct** **_timespec64**， **tv_sec**是 **__time64_t**值。 在  **struct** **timespec**， **tv_sec**是**time_t**類型，這是 32 位元或 64 位元長度取決於是否前置處理器定義巨集 _USE_32BIT_TIME_T。 **Timespec_get**函式是內嵌函式呼叫 **_timespec32_get**如果已定義 _USE_32BIT_TIME_T; 否則會呼叫 **_timespec64_get**。

**結束 Microsoft 專有**

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**timespec_get**， **_timespec32_get**， **_timespec64_get**|C: \<time.h>，C++： \<ctime> 或 \<time.h>|

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
