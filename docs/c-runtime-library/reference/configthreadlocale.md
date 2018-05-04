---
title: _configthreadlocale | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _configthreadlocale
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
- api-ms-win-crt-locale-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _configthreadlocale
- configthreadlocale
dev_langs:
- C++
helpviewer_keywords:
- configthreadlocale function
- locales, per-thread
- _configthreadlocale function
- per-thread locale
- thread locale
ms.assetid: 10e4050e-b587-4f30-80bc-6c76b35fc770
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7531a5849bc1e86d469a12747b5c4648b76c9117
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="configthreadlocale"></a>_configthreadlocale

設定個別執行緒地區設定選項。

## <a name="syntax"></a>語法

```C
int _configthreadlocale( int per_thread_locale_type );
```

### <a name="parameters"></a>參數

*per_thread_locale_type*<br/>
要設定的選項。 下表中列出的其中一個選項。

## <a name="return-value"></a>傳回值

先前的個別執行緒地區設定狀態 (**_DISABLE_PER_THREAD_LOCALE**或 **_ENABLE_PER_THREAD_LOCALE**)，則為-1 失敗。

## <a name="remarks"></a>備註

**_Configurethreadlocale**函數用來控制使用的執行緒特定地區設定。 使用下列其中一種*per_thread_locale_type*選項來指定，或判斷每個執行緒的地區設定狀態：

|||
|-|-|
**_ENABLE_PER_THREAD_LOCALE**|讓目前執行緒使用執行緒特定地區設定。 後續呼叫**setlocale**在這個執行緒會影響執行緒的地區設定。
**_DISABLE_PER_THREAD_LOCALE**|讓目前執行緒使用全域地區設定。 後續呼叫**setlocale**在這個執行緒會影響其他使用全域地區設定的執行緒。
**0**|擷取這個特定執行緒的目前設定。

這些函式會影響行為的**setlocale**， **_tsetlocale**， **_wsetlocale**，和 **_setmbcp**。 當每個執行緒的地區設定是已停用，任何後續呼叫**setlocale**或 **_wsetlocale**變更使用全域地區設定的所有執行緒的地區設定。 啟用個別執行緒地區設定時， **setlocale**或 **_wsetlocale**只會影響目前的執行緒地區設定。

如果您使用 **_configurethreadlocale**若要啟用個別執行緒地區設定，我們建議您呼叫**setlocale**或 **_wsetlocale**慣用的地區設定中的執行緒立即之後。

如果*per_thread_locale_type*不是其中一個值列於表格中，此函式會叫用無效參數處理常式中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，此函式會將**errno**至**EINVAL**並傳回-1。

## <a name="requirements"></a>需求

|常式|必要的標頭|
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
[多執行緒和地區設定](../../parallel/multithreading-and-locales.md)<br/>
