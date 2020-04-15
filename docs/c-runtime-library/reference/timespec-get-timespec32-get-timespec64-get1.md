---
title: timespec_get、_timespec32_get、_timespec64_get1
ms.date: 4/2/2020
api_name:
- timespec_get
- _timespec32_get
- _timespec64_get
- _o__timespec32_get
- _o__timespec64_get
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
ms.openlocfilehash: fc6d91b076f2dd2e25c55d9cf7062e81c3fab11a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362495"
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

如果成功,*則基*的值,否則返回零。

## <a name="remarks"></a>備註

**timespec_get**函數設置*time_spec*參數指向結構中的當前時間。 此結構的所有版本都有兩個成員 **,tv_sec**和**tv_nsec**。 **tv_sec**值設置為整個秒數 **,tv_nsec到**整數值的納秒,四捨五入到系統時鐘的解析度,因為*開始由基*指定的紀元。

**Microsoft 特定的**

這些函數僅支持作為*基*值**TIME_UTC。** 這將*time_spec*值設置為自紀元開始以來的秒數和納秒數,1970 年 1 月 1 日午夜,協調通用時間 (UTC)。 在**結構****_timespec32**中 **,tv_sec**是**一個__time32_t**值。 在**結構****_timespec64**中 **,tv_sec**是**一個__time64_t**值。 在**結構****時間光譜**中 **,tv_sec**是一**種time_t**類型,長度為 32 位或 64 位元,具體取決於是否定義了預處理器宏_USE_32BIT_TIME_T。 **timespec_get**函數是一個內聯函數,如果定義了_USE_32BIT_TIME_T,則調用 **_timespec32_get;** 否則它呼叫 **_timespec64_get**。

**結束 Microsoft 專有**

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**timespec_get** **_timespec32_get** **_timespec64_get**|C: \<time.h>，C++： \<ctime> 或 \<time.h>|

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
