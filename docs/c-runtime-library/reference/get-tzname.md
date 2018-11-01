---
title: _get_tzname
ms.date: 10/22/2018
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
helpviewer_keywords:
- _get_tzname function
- time zones
- get_tzname function
ms.assetid: df0065ff-095f-4237-832c-2fe9ab913875
ms.openlocfilehash: c173832efb866eed133a908b5f2b72266fd3798a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50452230"
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
字串長度*timeZoneName*包括 null 結束字元。

*timeZoneName*<br/>
根據時區名稱或日光節約標準時區名稱 (DST)，表示的字元字串的地址*index*。

*sizeInBytes*<br/>
大小*timeZoneName*字元字串，以位元組為單位。

*index*<br/>
要擷取的兩個時區名稱中，其中一個時區名稱的索引。

|*index*|內容*timeZoneName*|*timeZoneName*預設值|
|-|-|-|
|0|時區名稱|"PST"|
|1|日光節約標準時區名稱|"PDT"|
|> 1 或 < 0|**errno**設定為**EINVAL**|未修改|

除非在執行階段期間明確地變更值，否則預設值分別為 "PST" 和 "PDT"。

## <a name="return-value"></a>傳回值

如果成功，否則為**errno**輸入值。

如果有任一*timeZoneName*是**NULL**，或*sizeInBytes*為零或小於零 （但非兩者皆是），無效參數處理常式會叫用，如中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，此函式會將**errno**要**EINVAL** ，並傳回**EINVAL**。

### <a name="error-conditions"></a>錯誤狀況

|*pReturnValue*|*timeZoneName*|*sizeInBytes*|*index*|傳回值|內容*timeZoneName*|
|--------------------|--------------------|-------------------|-------------|------------------|--------------------------------|
|時區名稱的大小|**NULL**|0|0 或 1|0|未修改|
|時區名稱的大小|any|> 0|0 或 1|0|時區名稱|
|未修改|**NULL**|> 0|any|**EINVAL**|未修改|
|未修改|any|零|any|**EINVAL**|未修改|
|未修改|any|> 0|> 1|**EINVAL**|未修改|

## <a name="remarks"></a>備註

**_Get_tzname**函式會擷取目前的時區名稱或日光節約標準時區名稱 (DST) 的字元字串表示，轉換的地址*timeZoneName*取決於索引值，以及在字串的大小*pReturnValue*。 如果*timeZoneName*是**NULL**並*sizeInBytes*是為零，才能保留指定的時區字串的大小，並以位元組為單位結束的 null 會傳入*pReturnValue*。 索引值必須是標準時區的 0 或日光節約標準時區; 1任何其他值的*index*有未定的結果。

## <a name="example"></a>範例

此範例會呼叫 **_get_tzname**若要取得所需的緩衝區大小，以顯示目前日光節約標準時區名稱，會配置該大小的緩衝區，呼叫 **_get_tzname**以載入中的名稱緩衝區，並將它列印至主控台。

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

### <a name="output"></a>輸出

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
