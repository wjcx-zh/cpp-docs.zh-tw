---
title: _configthreadlocale
ms.date: 4/2/2020
api_name:
- _configthreadlocale
- _o__configthreadlocale
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
- api-ms-win-crt-locale-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _configthreadlocale
- configthreadlocale
helpviewer_keywords:
- configthreadlocale function
- locales, per-thread
- _configthreadlocale function
- per-thread locale
- thread locale
ms.assetid: 10e4050e-b587-4f30-80bc-6c76b35fc770
ms.openlocfilehash: 46983843e128b59df89722c8d4694c30a858011f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348548"
---
# <a name="_configthreadlocale"></a>_configthreadlocale

設定個別執行緒地區設定選項。

## <a name="syntax"></a>語法

```C
int _configthreadlocale( int per_thread_locale_type );
```

### <a name="parameters"></a>參數

*per_thread_locale_type*<br/>
要設定的選項。 下表中列出的其中一個選項。

## <a name="return-value"></a>傳回值

以前的每個線程區域設置狀態 **(_DISABLE_PER_THREAD_LOCALE**或 **_ENABLE_PER_THREAD_LOCALE),** 或失敗時為 -1。

## <a name="remarks"></a>備註

**_configurethreadlocale**函數用於控制線程特定區域設置的使用。 使用這些*per_thread_locale_type*選項的一指定或確定每個線程區域設定狀態:

| 選項 | 描述 |
|-|-|
| **_ENABLE_PER_THREAD_LOCALE** | 讓目前執行緒使用執行緒特定地區設定。 在此線程中**設置區域設置的**後續調用僅影響線程自己的區域設置。 |
| **_DISABLE_PER_THREAD_LOCALE** | 讓目前執行緒使用全域地區設定。 在此線程中**設置區域設置的**後續調用會影響使用全域區域設置的其他線程。 |
| **0** | 擷取這個特定執行緒的目前設定。 |

這些函數影響**集區域設置****、_tsetlocale、_wsetlocale**和 **_setmbcp**的行為 **_wsetlocale**。 禁用每個線程區域設置時,任何後續設置**區域設置**或 **_wsetlocale**調用都更改使用全域區域設置的所有線程的區域設置。 啟用每個線程區域設定時,**設定區域設定**或 **_wsetlocale**只會影響當前線程區域設置。

如果使用 **_configurethreadlocale**啟用每個線程區域設定,我們建議您調用**setlocale**或 **_wsetlocale,** 以便立即在該線程中設置首選區域設置。

如果*per_thread_locale_type*不是表中列出的值之一,則此函數將調用無效的參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,此函數將**errno**設置到**EINVAL**並返回 -1。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_configthreadlocale**|\<locale.h>|

## <a name="example"></a>範例

```cpp
// crt_configthreadlocale.cpp
//
// This program demonstrates the use of _configthreadlocale when
// using two independent threads.
//
// Compile by using: cl /EHsc /W4 crt_configthreadlocale.cpp

#include <locale.h>
#include <mbctype.h>
#include <process.h>
#include <windows.h>
#include <stdio.h>
#include <time.h>

#define BUFF_SIZE 100

// Retrieve the date and time in the current
// locale's format.
int get_time(unsigned char* str)
{
    __time64_t  ltime;
    struct tm   thetime;

    // Retieve the time
    _time64(&ltime);
    _gmtime64_s(&thetime, &ltime);

    // Format the current time structure into a string
    // using %#x is the long date representation,
    // appropriate to the current locale
    if (!strftime((char *)str, BUFF_SIZE, "%#x",
                  (const struct tm*)&thetime))
    {
        printf("strftime failed!\n");
        return -1;
    }
    return 0;
}

// This thread sets its locale to German
// and prints the time.
unsigned __stdcall SecondThreadFunc( void* /*pArguments*/ )
{
    unsigned char str[BUFF_SIZE];

    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);

    // Set the thread code page
    _setmbcp(_MB_CP_ANSI);

    // Set the thread locale
    printf("The thread locale is now set to %s.\n",
           setlocale(LC_ALL, "German"));

    // Retrieve the time string from the helper function
    if (get_time(str) == 0)
    {
        printf("The time in German locale is: '%s'\n", str);
    }

    _endthreadex( 0 );
    return 0;
}

// The main thread spawns a second thread (above) and then
// sets the locale to English and prints the time.
int main()
{
    HANDLE          hThread;
    unsigned        threadID;
    unsigned char   str[BUFF_SIZE];

    // Enable per-thread locale causes all subsequent locale
    // setting changes in this thread to only affect this thread.
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);

    // Retrieve the time string from the helper function
    printf("The thread locale is now set to %s.\n",
           setlocale(LC_ALL, "English"));

    // Create the second thread.
    hThread = (HANDLE)_beginthreadex( NULL, 0, &SecondThreadFunc,
                                      NULL, 0, &threadID );

    if (get_time(str) == 0)
    {
        // Retrieve the time string from the helper function
        printf("The time in English locale is: '%s'\n\n", str);
    }

    // Wait for the created thread to finish.
    WaitForSingleObject( hThread, INFINITE );

    // Destroy the thread object.
    CloseHandle( hThread );
}
```

```Output
The thread locale is now set to English_United States.1252.
The time in English locale is: 'Wednesday, May 12, 2004'

The thread locale is now set to German_Germany.1252.
The time in German locale is: 'Mittwoch, 12. Mai 2004'
```

## <a name="see-also"></a>另請參閱

[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[_beginthread、_beginthreadex](beginthread-beginthreadex.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[多線緒與區域設定](../../parallel/multithreading-and-locales.md)<br/>
