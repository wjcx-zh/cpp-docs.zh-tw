---
title: _get_dstbias
ms.date: 11/04/2016
api_name:
- _get_dstbias
- __dstbias
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
- __dstbias
- _get_dstbias
- get_dstbias
helpviewer_keywords:
- __dstbias
- daylight saving time offset
- get_dstbias function
- _get_dstbias function
ms.assetid: e751358c-1ecc-411b-ae2c-81b2ec54ea45
ms.openlocfilehash: a48cc4fe35a1bbd18342750571214ed0977cf3ee
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955942"
---
# <a name="_get_dstbias"></a>_get_dstbias

擷取日光節約時間位移 (秒)。

## <a name="syntax"></a>語法

```C
error_t _get_dstbias( int* seconds );
```

### <a name="parameters"></a>參數

*表示*<br/>
日光節約時間的位移 (秒)。

## <a name="return-value"></a>傳回值

如果成功，則為零; 如果發生錯誤，則為**errno**值。

## <a name="remarks"></a>備註

**_Get_dstbias**函數會將日光節約時間中的秒數視為整數。 若日光節約時間已生效，則預設位移為 3600 秒，此為一小時的秒數 (但少數地區是遵循兩小時的位移)。

如果*秒數*為**Null**，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，此函式會將**errno**設定為**EINVAL** ，並傳回**EINVAL**。

建議您使用此函式，而不是使用宏 **_dstbias**或已被取代的函數 **__dstbias**。

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
