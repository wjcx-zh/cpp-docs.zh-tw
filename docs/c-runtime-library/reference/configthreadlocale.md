---
title: _configthreadlocale | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 24
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 1fca01932efb2f80d4aebf94db8900cee5d79805
ms.lasthandoff: 02/24/2017

---
# <a name="configthreadlocale"></a>_configthreadlocale
設定個別執行緒地區設定選項。  
  
## <a name="syntax"></a>語法  
  
```  
int _configthreadlocale(  
   int type  
);  
```  
  
### <a name="parameters"></a>參數  
 `type`  
 要設定的選項。 下表中列出的其中一個選項。  
  
## <a name="return-value"></a>傳回值  
 前一個個別執行緒地區設定狀態 (`_DISABLE_PER_THREAD_LOCALE` 或 `_ENABLE_PER_THREAD_LOCALE`)，失敗時則為 -1。  
  
## <a name="remarks"></a>備註  
 `_configurethreadlocale` 函式用來控制如何使用執行緒特定地區設定。 您可以使用其中一個選項來指定或判斷個別執行緒地區設定狀態︰  
  
 `_ENABLE_PER_THREAD_LOCALE`  
 讓目前執行緒使用執行緒特定地區設定。 此執行緒中的後續 `setlocale` 呼叫只會影響執行緒自己的地區設定。  
  
 `_DISABLE_PER_THREAD_LOCALE`  
 讓目前執行緒使用全域地區設定。 此執行緒中的後續 `setlocale` 呼叫會影響使用全域地區設定的其他執行緒。  
  
 `0`  
 擷取這個特定執行緒的目前設定。  
  
 這些函式會影響行為的`setlocale`， `_tsetlocale`，和`_wsetlocale`。 每個執行緒的地區設定時停用，任何後續呼叫`setlocale`或`_wsetlocale`變更使用全域地區設定的所有執行緒的地區設定。 啟用個別執行緒地區設定時，`setlocale` 或 `_wsetlocale` 只會影響目前執行緒的地區設定。  
  
 如果您使用 `_configurethreadlocale` 啟用個別執行緒地區設定，則建議您呼叫 `setlocale` 或 `_wsetlocale` 立即在該執行緒中設定慣用地區設定。  
  
 如果 `type` 不是表格中所列的其中一個值，則此函式會叫用無效的參數處理常式 (如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述)。 若允許繼續執行，此函式會將 `errno` 設為 `EINVAL`，並傳回 -1。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_configthreadlocale`|\<locale.h>|  
  
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
 [setlocale、_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [_beginthread、_beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [多執行緒和地區設定](../../parallel/multithreading-and-locales.md)  

