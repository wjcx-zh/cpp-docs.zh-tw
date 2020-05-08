---
title: _get_timezone
ms.date: 4/2/2020
api_name:
- _get_timezone
- _o__get_timezone
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _get_timezone
- get_timezone
helpviewer_keywords:
- time zones
- get_timezone function
- _get_timezone function
ms.assetid: 30ab0838-0ae9-4a2f-bfe6-a49ee443b21e
ms.openlocfilehash: 28838825ab7a15f312f5f75a8ad9166926979690
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918505"
---
# <a name="_get_timezone"></a>_get_timezone

擷取國際標準時間 (UTC) 和當地時間之間的時差，以秒為單位。

## <a name="syntax"></a>語法

```C
error_t _get_timezone(
    long* seconds
);
```

### <a name="parameters"></a>參數

*表示*<br/>
UTC 與當地時間之間的時差，以秒為單位。

## <a name="return-value"></a>傳回值

如果成功，則為零; 如果發生錯誤，則為**errno**值。

## <a name="remarks"></a>備註

**_Get_timezone**函式會以秒為單位，抓取 UTC 與本地時間之間的時差。 對太平洋標準時間而言，預設值為 28,800 秒 (晚 UTC 八小時)。

如果*秒數*為**Null**，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，此函式會將**errno**設定為**EINVAL** ，並傳回**EINVAL**。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_get_timezone**|\<time.h>|

如需詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[時間管理](../../c-runtime-library/time-management.md)<br/>
[errno、_doserrno、_sys_errlist，和_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_daylight](get-daylight.md)<br/>
[_get_dstbias](get-dstbias.md)<br/>
[_get_tzname](get-tzname.md)<br/>
