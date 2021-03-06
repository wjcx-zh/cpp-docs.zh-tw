---
title: _get_daylight
ms.date: 4/2/2020
api_name:
- __daylight
- _get_daylight
- _o___daylight
- _o__get_daylight
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
- get_daylight
- _get_daylight
helpviewer_keywords:
- get_daylight function
- daylight saving time offset
- _get_daylight function
ms.assetid: f85a6ba3-e187-4ca7-aed7-ffc694c8ac4c
ms.openlocfilehash: 226242c5dd6c3c204d2449bd14ee7dee4f5fe7b5
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919392"
---
# <a name="_get_daylight"></a>_get_daylight

擷取日光節約時間位移 (小時)。

## <a name="syntax"></a>語法

```C
error_t _get_daylight( int* hours );
```

### <a name="parameters"></a>參數

*多少*<br/>
日光節約時間的位移 (小時)。

## <a name="return-value"></a>傳回值

如果成功，則為零; 如果發生錯誤，則為**errno**值。

## <a name="remarks"></a>備註

**_Get_daylight**函式會將日光節約時間中的時數，以整數形式抓取。 若日光節約時間已生效，則預設位移為一小時 (但少數地區是遵循兩小時的位移)。

如果*hours*為**Null**，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，此函式會將**errno**設定為**EINVAL** ，並傳回**EINVAL**。

建議您使用此函式，而不是使用宏 **_daylight**或已被取代的函式 **__daylight**。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_get_daylight**|\<time.h>|

如需詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[時間管理](../../c-runtime-library/time-management.md)<br/>
[errno、_doserrno、_sys_errlist，和_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_dstbias](get-dstbias.md)<br/>
[_get_timezone](get-timezone.md)<br/>
[_get_tzname](get-tzname.md)<br/>
