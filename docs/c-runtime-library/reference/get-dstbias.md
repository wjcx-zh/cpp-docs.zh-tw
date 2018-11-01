---
title: _get_dstbias
ms.date: 11/04/2016
apiname:
- _get_dstbias
- __dstbias
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
- __dstbias
- _get_dstbias
- get_dstbias
helpviewer_keywords:
- __dstbias
- daylight saving time offset
- get_dstbias function
- _get_dstbias function
ms.assetid: e751358c-1ecc-411b-ae2c-81b2ec54ea45
ms.openlocfilehash: 61807f854dc9c2f7de6f0acd5bbf4668987ce49e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50579098"
---
# <a name="getdstbias"></a>_get_dstbias

擷取日光節約時間位移 (秒)。

## <a name="syntax"></a>語法

```C
error_t _get_dstbias( int* seconds );
```

### <a name="parameters"></a>參數

*秒數*<br/>
日光節約時間的位移 (秒)。

## <a name="return-value"></a>傳回值

如果成功，或在為零**errno**值發生錯誤。

## <a name="remarks"></a>備註

**_Get_dstbias**函式會擷取為整數的日光節約時間的秒數。 若日光節約時間已生效，則預設位移為 3600 秒，此為一小時的秒數 (但少數地區是遵循兩小時的位移)。

如果*秒*是**NULL**，會叫用無效參數處理常式，如中所述[Parameter Validation](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，此函式會將**errno**要**EINVAL** ，並傳回**EINVAL**。

我們建議您利用這個函數，而不是巨集 **_dstbias**或 已被取代的函式 **__dstbias**。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_get_dstbias**|\<time.h>|

如需詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[時間管理](../../c-runtime-library/time-management.md)<br/>
[errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_daylight](get-daylight.md)<br/>
[_get_timezone](get-timezone.md)<br/>
[_get_tzname](get-tzname.md)<br/>
