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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 26bcfe0d93a8c2b1a14e6afc0d413a5c7e4a7f6e
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917311"
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

先前的每一線程地區設定狀態（**_DISABLE_PER_THREAD_LOCALE**或 **_ENABLE_PER_THREAD_LOCALE**），或失敗時為-1。

## <a name="remarks"></a>備註

**_Configurethreadlocale**函數是用來控制執行緒特定地區設定的使用。 使用下列其中一個*per_thread_locale_type*選項來指定或決定每個執行緒的地區設定狀態：

| 選項 | 描述 |
|-|-|
| **_ENABLE_PER_THREAD_LOCALE** | 讓目前執行緒使用執行緒特定地區設定。 在此執行緒中的後續呼叫**setlocale**只會影響執行緒本身的地區設定。 |
| **_DISABLE_PER_THREAD_LOCALE** | 讓目前執行緒使用全域地區設定。 後續呼叫此執行緒中的**setlocale**會影響使用全域地區設定的其他執行緒。 |
| **0** | 擷取這個特定執行緒的目前設定。 |

這些函數會影響**setlocale**、 **_tsetlocale**、 **_wsetlocale**和 **_setmbcp**的行為。 停用個別執行緒地區設定時，任何後續對**setlocale**或 **_wsetlocale**的呼叫都會變更使用全域地區設定之所有線程的地區設定。 啟用每個執行緒的地區設定時， **setlocale**或 **_wsetlocale**只會影響目前線程的地區設定。

如果您使用 **_configurethreadlocale**來啟用每個執行緒的地區設定，建議您呼叫**setlocale**或 **_wsetlocale** ，以便在該執行緒之後立即設定慣用的地區設定。

如果*per_thread_locale_type*不是資料表中所列的其中一個值，則此函式會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，此函式會將**errno**設定為**EINVAL** ，並傳回-1。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

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
[語言](../../c-runtime-library/locale.md)<br/>
[多執行緒和地區設定](../../parallel/multithreading-and-locales.md)<br/>
