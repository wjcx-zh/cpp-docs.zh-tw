---
title: _get_tzname | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _get_tzname
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
- _get_tzname
- get_tzname
dev_langs:
- C++
helpviewer_keywords:
- _get_tzname function
- time zones
- get_tzname function
ms.assetid: df0065ff-095f-4237-832c-2fe9ab913875
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2a3a9fc2b90ac9e52a78613bc8ccfcd24b9acb56
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="gettzname"></a>_get_tzname

擷取代表時區名稱或日光節約標準時區名稱 (DST) 的字元字串。

## <a name="syntax"></a>語法

```C
errno_t _get_tzname(
    size_t* pReturnValue,
    char* timeZoneName,
    size_t sizeInBytes,
    int index
);
```

### <a name="parameters"></a>參數

*pReturnValue*<br/>
字串長度*timeZoneName*包括 NULL 結束字元。

*timeZoneName*<br/>
字元字串來表示時區名稱或日光節約標準時間區域名稱 (DST)，取決於位址*索引*。

*sizeInBytes*<br/>
大小*timeZoneName*字元字串，以位元組為單位。

*index*<br/>
要擷取的兩個時區名稱中，其中一個時區名稱的索引。

## <a name="return-value"></a>傳回值

如果成功，否則**errno**輸入值。

如果有任一個*timeZoneName*是**NULL**，或*sizeInBytes*為零，或小於零 （但非兩者皆是）、 無效參數處理常式會叫用中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，此函式會將**errno**至**EINVAL**並傳回**EINVAL**。

### <a name="error-conditions"></a>錯誤狀況

|*pReturnValue*|*timeZoneName*|*sizeInBytes*|*index*|傳回值|內容*timeZoneName*|
|--------------------|--------------------|-------------------|-------------|------------------|--------------------------------|
|時區名稱的大小|**NULL**|0|0 或 1|0|未修改|
|時區名稱的大小|任何|> 0|0 或 1|0|時區名稱|
|未修改|**NULL**|> 0|任何|**EINVAL**|未修改|
|未修改|任何|零|任何|**EINVAL**|未修改|
|未修改|任何|> 0|> 1|**EINVAL**|未修改|

## <a name="remarks"></a>備註

**_Get_tzname**函式會擷取的字元字串表示時區名稱或日光節約標準時間區域名稱 (DST) 的位址*timeZoneName*根據索引值在字串的大小以及*pReturnValue*。 如果*timeZoneName*是**NULL**和*sizeInBytes*是零，以位元組為單位的區域中，會傳回其中一個時間字串的大小*pReturnValue*. 標準時區的索引值必須為 0 或日光節約標準時區的索引值必須為 1；任何索引的其他值均為未定結果。

### <a name="index-values"></a>索引值

|*index*|內容*timeZoneName*|*timeZoneName*預設值|
|-------------|--------------------------------|----------------------------------|
|0|時區名稱|"PST"|
|1|日光節約標準時區名稱|"PDT"|
|> 1 或 < 0|**errno**設**EINVAL**|未修改|

除非在執行階段期間明確地變更值，否則預設值分別為 "PST" 和 "PDT"。  這些字元陣列的大小都受到**TZNAME_MAX**值。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_get_tzname**|\<time.h>|

如需詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[時間管理](../../c-runtime-library/time-management.md)<br/>
[errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_daylight](get-daylight.md)<br/>
[_get_dstbias](get-dstbias.md)<br/>
[_get_timezone](get-timezone.md)<br/>
[TZNAME_MAX](../../c-runtime-library/tzname-max.md)<br/>
