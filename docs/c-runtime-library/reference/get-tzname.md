---
title: _get_tzname
ms.date: 4/2/2020
api_name:
- _get_tzname
- _o__get_tzname
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
- _get_tzname
- get_tzname
helpviewer_keywords:
- _get_tzname function
- time zones
- get_tzname function
ms.assetid: df0065ff-095f-4237-832c-2fe9ab913875
ms.openlocfilehash: 50f1f6e4320e3ef905b4eda67ba1d458a5b1df08
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344879"
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

*p 傳回值*<br/>
*時區名稱*的字串長度,包括空終止符。

*時區名稱*<br/>
表示時區名稱或日光標準時區名稱 (DST) 的字串位址,具體取決於*索引*。

*大小位元組*<br/>
以位元組為單位*的時區名稱*字串的大小。

*指數*<br/>
要擷取的兩個時區名稱中，其中一個時區名稱的索引。

|*指數*|*時區名稱*的內容|*時區名稱*預設值|
|-|-|-|
|0|時區名稱|"PST"|
|1|日光節約標準時區名稱|"PDT"|
|> 1 或 < 0|**errno**設定為**EINVAL**|未修改|

除非在執行階段期間明確地變更值，否則預設值分別為 "PST" 和 "PDT"。

## <a name="return-value"></a>傳回值

如果成功,則為零,否則為**errno**類型值。

如果任*一時區名稱*為**NULL**,或者*sizeInBytes*為零或小於零(但不是兩者),則調用無效的參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許執行繼續,此函數將**errno**設定到**EINVAL**並傳回**EINVAL**。

### <a name="error-conditions"></a>錯誤狀況

|*p 傳回值*|*時區名稱*|*大小位元組*|*指數*|傳回值|*時區名稱*的內容|
|--------------------|--------------------|-------------------|-------------|------------------|--------------------------------|
|時區名稱的大小|**空**|0|0 或 1|0|未修改|
|時區名稱的大小|任意|> 0|0 或 1|0|時區名稱|
|未修改|**空**|> 0|任意|**埃因瓦爾**|未修改|
|未修改|任意|零|任意|**埃因瓦爾**|未修改|
|未修改|任意|> 0|> 1|**埃因瓦爾**|未修改|

## <a name="remarks"></a>備註

**_get_tzname**函數根據索引值將當前時區名稱或日光標準時區名稱 (DST) 的字串表示形式檢索到*時區名稱*的位址,以及*pReturnValue*中的字串大小。 如果*timeZoneName*為*NULL,並且大小 InBytes*為零,則在*pReturnValue*中傳回儲存指定時區和終止**NULL**null 的字串的大小。 對於標準時區,索引值必須為 0,對於日光標準時區,索引值必須為 1;*索引*的任何其他值都有不確定的結果。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="example"></a>範例

此示例調用 **_get_tzname**以獲取所需的緩衝區大小以顯示當前 Daylight 標準時區名稱、分配該大小的緩衝區、再次調用 **_get_tzname**以在緩衝區中載入名稱並將其列印到主控台。

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

如需詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[時間管理](../../c-runtime-library/time-management.md)<br/>
[errno、_doserrno、_sys_errlist，和_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_daylight](get-daylight.md)<br/>
[_get_dstbias](get-dstbias.md)<br/>
[_get_timezone](get-timezone.md)<br/>
