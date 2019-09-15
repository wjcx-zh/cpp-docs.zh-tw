---
title: _get_tzname
ms.date: 10/22/2018
api_name:
- _get_tzname
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
- _get_tzname
- get_tzname
helpviewer_keywords:
- _get_tzname function
- time zones
- get_tzname function
ms.assetid: df0065ff-095f-4237-832c-2fe9ab913875
ms.openlocfilehash: 9f86a4997c328e86597e3bad8a7f7a3a5f5f50b6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955618"
---
# <a name="_get_tzname"></a>_get_tzname

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
*TimeZoneName*的字串長度，包括 null 結束字元。

*timeZoneName*<br/>
表示時區名稱或日光節約標準時區名稱（DST）的字元字串位址，視*索引*而定。

*sizeInBytes*<br/>
*TimeZoneName*字元字串的大小（以位元組為單位）。

*index*<br/>
要擷取的兩個時區名稱中，其中一個時區名稱的索引。

|*index*|*TimeZoneName*的內容|*timeZoneName*預設值|
|-|-|-|
|0|時區名稱|"PST"|
|1|日光節約標準時區名稱|"PDT"|
|> 1 或 < 0|**errno**設定為**EINVAL**|未修改|

除非在執行階段期間明確地變更值，否則預設值分別為 "PST" 和 "PDT"。

## <a name="return-value"></a>傳回值

如果成功，則為零，否則為**errno**類型值。

如果其中一個*timeZoneName*是**Null**，或是*sizeInBytes*是零或小於零（但不是兩者），則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，此函式會將**errno**設定為**EINVAL** ，並傳回**EINVAL**。

### <a name="error-conditions"></a>錯誤狀況

|*pReturnValue*|*timeZoneName*|*sizeInBytes*|*index*|傳回值|*TimeZoneName*的內容|
|--------------------|--------------------|-------------------|-------------|------------------|--------------------------------|
|時區名稱的大小|**NULL**|0|0 或 1|0|未修改|
|時區名稱的大小|any|> 0|0 或 1|0|時區名稱|
|未修改|**NULL**|> 0|any|**EINVAL**|未修改|
|未修改|any|零|any|**EINVAL**|未修改|
|未修改|any|> 0|> 1|**EINVAL**|未修改|

## <a name="remarks"></a>備註

**_Get_tzname**函式會根據索引值，將目前時區名稱或日游標準時區名稱（DST）的字元字串表示，捕獲到*timeZoneName*的位址，以及中的字串大小。*pReturnValue*。 如果*timeZoneName*為**Null** ，而*sizeInBytes*為零，則在*pReturnValue*中會傳回用來保存指定時區和終止 Null （以位元組為單位）的字串大小。 標準時區的索引值必須是0或日光節約標準時區的1。*索引*的任何其他值都有未確定的結果。

## <a name="example"></a>範例

這個範例會呼叫 **_get_tzname**來取得所需的緩衝區大小，以顯示目前的日游標準時區名稱、配置該大小的緩衝區、再次呼叫 **_get_tzname**以載入緩衝區中的名稱，並將它列印到主控台。

```C
// crt_get_tzname.c
// Compile by using: cl /W4 crt_get_tzname.c
#include <stdio.h>
#include <time.h>
#include <malloc.h>

enum TZINDEX {
    STD,
    DST
};

int main()
{
    size_t tznameSize = 0;
    char * tznameBuffer = NULL;

    // Get the size of buffer required to hold DST time zone name
    if (_get_tzname(&tznameSize, NULL, 0, DST))
        return 1;    // Return an error value if it failed

    // Allocate a buffer for the name
    if (NULL == (tznameBuffer = (char *)(malloc(tznameSize))))
        return 2;    // Return an error value if it failed

    // Load the name in the buffer
    if (_get_tzname(&tznameSize, tznameBuffer, tznameSize, DST))
        return 3;    // Return an error value if it failed

    printf_s("The current Daylight standard time zone name is %s.\n", tznameBuffer);
    return 0;
}
```

### <a name="output"></a>Output

```Output
The current Daylight standard time zone name is PDT.
```

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_get_tzname**|\<time.h>|

如需詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[時間管理](../../c-runtime-library/time-management.md)<br/>
[errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_daylight](get-daylight.md)<br/>
[_get_dstbias](get-dstbias.md)<br/>
[_get_timezone](get-timezone.md)<br/>
