---
title: "timespec_get、_timespec32_get、_timespec64_get1 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
helpviewer_keywords:
- timespec_get function
- _timespec32_get function
- _timespec64_get function
ms.assetid: ed757258-b4f2-4c1d-a91b-22ea6ffce4ab
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 681f9d125a7f45dae2a8e604df655facdd246067
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="timespecget-timespec32get-timespec64get"></a>timespec_get、_timespec32_get、_timespec64_get
使用第一個引數，依據指定的時間基礎，將間隔設定成指向目前的月曆時間。  
  
## <a name="syntax"></a>語法  
  
```  
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
  
#### <a name="parameters"></a>參數  
 `time_spec`  
 設定為自 Epoch 啟動後所經歷之時間 (以秒及奈秒為單位) 的結構指標。  
  
 `base`  
 非零實作的專用值，會指定時間依據。  
  
## <a name="return-value"></a>傳回值  
 若成功，會傳回 `base` 的值，否則會傳回零。  
  
## <a name="remarks"></a>備註  
 `timespec_get` 函式會透過 `time_spec` 引數，將指向的結構設為目前的時間。 此結構的所有版本皆具有 `tv_sec` 與 `tv_nsec`兩個成員。 `tv_sec` 值會設為自 `tv_nsec` 指定之 Epoch 啟動之後所經歷的秒數 (整數)，而 `base`值則會設為奈秒數 (整數)，並四捨五入到系統時鐘的解析度。  
  
 **Microsoft 特定的**  
  
 這些函式只可以 `TIME_UTC` 的 `base` 值提供支援。 這會將 `time_spec` 值設定為自 Epoch 啟動之後 (國際標準時間 (UTC) 1970 年 1 月 1 日的午夜) 所經歷的秒數與奈秒數。 在 `struct _timespec32`中， `tv_sec` 為 `__time32_t` 值。 在 `struct _timespec64`中， `tv_sec` 為 `__time64_t` 值。 在 `struct timespec`, ， `tv_sec` 為 `time_t` 類型，其長度為 32 位元或 64 位元，取決於有無定義前置處理器巨集 _USE_32BIT_TIME_T。 `timespec_get` 函式是內嵌函式。如有定義 _USE_32BIT_TIME_T，將會呼叫 `_timespec32_get` ，否則會呼叫 `_timespec64_get`。  
  
 **結束 Microsoft 專有**  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`timespec_get`中， `_timespec32_get`中， `_timespec64_get`|C: \<time.h>，C++： \<ctime> 或 \<time.h>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>請參閱  
 [時間管理](../../c-runtime-library/time-management.md)   
 [asctime、_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [asctime_s、_wasctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [_ftime、_ftime32、_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime、_gmtime32、_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [gmtime_s、_gmtime32_s、_gmtime64_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime、_localtime32、_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [localtime_s、_localtime32_s、_localtime64_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [time、_time32、_time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [_utime、_utime32、_utime64、_wutime、_wutime32、_wutime64](../../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md)