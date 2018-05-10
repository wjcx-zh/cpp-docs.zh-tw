---
title: 多執行緒和地區設定 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- locales [C++], multithreading
- multithreading [C++], locales
- threading [C++], locales
- per-thread locale
ms.assetid: d6fb159a-eaca-4130-a51a-f95d62f71485
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 19cc3817faab71c209586ad952162229f846e0a7
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="multithreading-and-locales"></a>多執行緒和地區設定
C 執行階段程式庫和 c + + 標準程式庫提供支援變更程式的地區設定。 本主題討論使用多執行緒應用程式中的兩個程式庫的地區設定功能時，會發生的問題。  
  
## <a name="remarks"></a>備註  
 C 執行階段程式庫，您可以建立多執行緒應用程式使用`_beginthread`和`_beginthreadex`函式。 本主題只涵蓋使用這些函數所建立的多執行緒應用程式。 如需詳細資訊，請參閱[_beginthread、 _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)。  
  
 若要變更使用 C 執行階段程式庫的地區設定，請使用[setlocale](../preprocessor/setlocale.md)函式。 在舊版的 Visual c + + 中，此函式一定會修改整個應用程式的地區設定。 沒有現可支援在個別執行緒上設定地區設定。 這是使用[_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md)函式。 若要指定[setlocale](../preprocessor/setlocale.md)應該只在變更目前的執行緒呼叫中的地區設定`_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`該執行緒中。 相反地，呼叫`_configthreadlocale(_DISABLE_PER_THREAD_LOCALE)`會導致使用全域地區設定，該執行緒，而且任何呼叫[setlocale](../preprocessor/setlocale.md) ，執行緒將會變更中未明確地啟用個別執行緒地區設定的所有執行緒的地區設定。  
  
 若要變更使用 c + + 執行階段程式庫的地區設定，請使用[locale 類別](../standard-library/locale-class.md)。 藉由呼叫[locale:: global](../standard-library/locale-class.md#global)方法中，變更中尚未明確地啟用個別執行緒地區設定的每個執行緒的地區設定。 若要變更的地區設定中的單一執行緒或應用程式的一部分，只要建立的執行個體`locale`執行緒或一部分的程式碼中的物件。  
  
> [!NOTE]
>  呼叫[locale:: global](../standard-library/locale-class.md#global) c + + 標準程式庫和 C 執行階段程式庫中變更地區設定。 不過，呼叫[setlocale](../preprocessor/setlocale.md)只會針對 C 執行階段程式庫; c + + 標準程式庫並不會影響變更地區設定。  
  
 下列範例顯示如何使用[setlocale](../preprocessor/setlocale.md)函式， [locale 類別](../standard-library/locale-class.md)，而[_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md)函式中的應用程式的地區設定的變更數個不同的案例。  
  
## <a name="example"></a>範例  
 在此範例中，主執行緒會繁衍兩個子執行緒。 第一個執行緒的執行緒，讓每個執行緒的地區設定，藉由呼叫`_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`。 第二個執行緒、 執行緒 B，以及主執行緒中，請勿啟用個別執行緒地區設定。 然後繼續進行變更地區設定使用的執行緒[setlocale](../preprocessor/setlocale.md)函式的 C 執行階段程式庫。  
  
 因為執行緒的每個執行緒的地區設定啟用，只有在使用 「 法文 」 的地區設定的執行緒 A 入門 C 執行階段程式庫函式。 主執行緒和執行緒 B 中的 C 執行階段程式庫函式，繼續使用"C"地區設定。 此外，因為[setlocale](../preprocessor/setlocale.md)不會影響 c + + 標準程式庫地區設定，所有 c + + 標準程式庫物件會繼續使用"C"地區設定。  
  
```  
// multithread_locale_1.cpp  
// compile with: /EHsc /MD  
#include <clocale>  
#include <cstdio>  
#include <locale>  
#include <process.h>  
#include <windows.h>  
  
#define NUM_THREADS 2  
using namespace std;  
  
unsigned __stdcall RunThreadA(void *params);  
unsigned __stdcall RunThreadB(void *params);  
  
BOOL localeSet = FALSE;  
HANDLE printMutex = CreateMutex(NULL, FALSE, NULL);  
  
int main()  
{  
    HANDLE threads[NUM_THREADS];  
  
    unsigned aID;  
    threads[0] = (HANDLE)_beginthreadex(  
        NULL, 0, RunThreadA, NULL, 0, &aID);  
  
    unsigned bID;  
    threads[1] = (HANDLE)_beginthreadex(  
        NULL, 0, RunThreadB, NULL, 0, &bID);  
  
    WaitForMultipleObjects(2, threads, TRUE, INFINITE);  
  
    printf_s("[Thread main] Per-thread locale is NOT enabled.\n");  
    printf_s("[Thread main] CRT locale is set to \"%s\"\n",  
        setlocale(LC_ALL, NULL));  
    printf_s("[Thread main] locale::global is set to \"%s\"\n",  
        locale().name().c_str());  
  
    CloseHandle(threads[0]);  
    CloseHandle(threads[1]);  
    CloseHandle(printMutex);  
  
    return 0;  
}  
  
unsigned __stdcall RunThreadA(void *params)  
{  
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);  
    setlocale(LC_ALL, "french");  
    localeSet = TRUE;  
  
    WaitForSingleObject(printMutex, INFINITE);  
    printf_s("[Thread A] Per-thread locale is enabled.\n");  
    printf_s("[Thread A] CRT locale is set to \"%s\"\n",  
        setlocale(LC_ALL, NULL));  
    printf_s("[Thread A] locale::global is set to \"%s\"\n\n",  
        locale().name().c_str());  
    ReleaseMutex(printMutex);  
  
    return 1;  
}  
  
unsigned __stdcall RunThreadB(void *params)  
{  
    while (!localeSet)  
        Sleep(100);  
  
    WaitForSingleObject(printMutex, INFINITE);  
    printf_s("[Thread B] Per-thread locale is NOT enabled.\n");  
    printf_s("[Thread B] CRT locale is set to \"%s\"\n",  
        setlocale(LC_ALL, NULL));  
    printf_s("[Thread B] locale::global is set to \"%s\"\n\n",  
        locale().name().c_str());  
    ReleaseMutex(printMutex);  
  
    return 1;  
}  
```  
  
```Output  
[Thread A] Per-thread locale is enabled.  
[Thread A] CRT locale is set to "French_France.1252"  
[Thread A] locale::global is set to "C"  
  
[Thread B] Per-thread locale is NOT enabled.  
[Thread B] CRT locale is set to "C"  
[Thread B] locale::global is set to "C"  
  
[Thread main] Per-thread locale is NOT enabled.  
[Thread main] CRT locale is set to "C"  
[Thread main] locale::global is set to "C"  
```  
  
## <a name="example"></a>範例  
 在此範例中，主執行緒會繁衍兩個子執行緒。 第一個執行緒的執行緒，讓每個執行緒的地區設定，藉由呼叫`_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`。 第二個執行緒、 執行緒 B，以及主執行緒中，請勿啟用個別執行緒地區設定。 然後繼續進行變更地區設定使用的執行緒[locale:: global](../standard-library/locale-class.md#global)方法的 c + + 標準程式庫。  
  
 因為執行緒的每個執行緒的地區設定啟用，只有在使用 「 法文 」 的地區設定的執行緒 A 入門 C 執行階段程式庫函式。 主執行緒和執行緒 B 中的 C 執行階段程式庫函式，繼續使用"C"地區設定。 不過，由於[locale:: global](../standard-library/locale-class.md#global)方法變更地區設定 「 全域 」，則所有的執行緒中所有 c + + 標準程式庫物件可讓您開始使用 「 法文 」 的地區設定。  
  
```  
// multithread_locale_2.cpp  
// compile with: /EHsc /MD  
#include <clocale>  
#include <cstdio>  
#include <locale>  
#include <process.h>  
#include <windows.h>  
  
#define NUM_THREADS 2  
using namespace std;  
  
unsigned __stdcall RunThreadA(void *params);  
unsigned __stdcall RunThreadB(void *params);  
  
BOOL localeSet = FALSE;  
HANDLE printMutex = CreateMutex(NULL, FALSE, NULL);  
  
int main()  
{  
    HANDLE threads[NUM_THREADS];  
  
    unsigned aID;  
    threads[0] = (HANDLE)_beginthreadex(  
        NULL, 0, RunThreadA, NULL, 0, &aID);  
  
    unsigned bID;  
    threads[1] = (HANDLE)_beginthreadex(  
        NULL, 0, RunThreadB, NULL, 0, &bID);  
  
    WaitForMultipleObjects(2, threads, TRUE, INFINITE);  
  
    printf_s("[Thread main] Per-thread locale is NOT enabled.\n");  
    printf_s("[Thread main] CRT locale is set to \"%s\"\n",  
        setlocale(LC_ALL, NULL));  
    printf_s("[Thread main] locale::global is set to \"%s\"\n",  
        locale().name().c_str());  
  
    CloseHandle(threads[0]);  
    CloseHandle(threads[1]);  
    CloseHandle(printMutex);  
  
    return 0;  
}  
  
unsigned __stdcall RunThreadA(void *params)  
{  
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);  
    locale::global(locale("french"));  
    localeSet = TRUE;  
  
    WaitForSingleObject(printMutex, INFINITE);  
    printf_s("[Thread A] Per-thread locale is enabled.\n");  
    printf_s("[Thread A] CRT locale is set to \"%s\"\n",  
        setlocale(LC_ALL, NULL));  
    printf_s("[Thread A] locale::global is set to \"%s\"\n\n",  
        locale().name().c_str());  
    ReleaseMutex(printMutex);  
  
    return 1;  
}  
  
unsigned __stdcall RunThreadB(void *params)  
{  
    while (!localeSet)  
        Sleep(100);  
  
    WaitForSingleObject(printMutex, INFINITE);  
    printf_s("[Thread B] Per-thread locale is NOT enabled.\n");  
    printf_s("[Thread B] CRT locale is set to \"%s\"\n",  
        setlocale(LC_ALL, NULL));  
    printf_s("[Thread B] locale::global is set to \"%s\"\n\n",  
        locale().name().c_str());  
    ReleaseMutex(printMutex);  
  
    return 1;  
}  
```  
  
```Output  
[Thread A] Per-thread locale is enabled.  
[Thread A] CRT locale is set to "French_France.1252"  
[Thread A] locale::global is set to "French_France.1252"  
  
[Thread B] Per-thread locale is NOT enabled.  
[Thread B] CRT locale is set to "C"  
[Thread B] locale::global is set to "French_France.1252"  
  
[Thread main] Per-thread locale is NOT enabled.  
[Thread main] CRT locale is set to "C"  
[Thread main] locale::global is set to "French_France.1252"  
```  
  
## <a name="example"></a>範例  
 在此範例中，主執行緒會繁衍兩個子執行緒。 第一個執行緒的執行緒，讓每個執行緒的地區設定，藉由呼叫`_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`。 第二個執行緒、 執行緒 B，以及主執行緒中，請勿啟用個別執行緒地區設定。 執行緒 B，然後繼續進行變更地區設定使用[setlocale](../preprocessor/setlocale.md)函式的 C 執行階段程式庫。  
  
 由於執行緒 B 不需要啟用個別執行緒地區設定，主執行緒和執行緒 B 中的 C 執行階段程式庫函式會開始使用 「 法文 」 的地區設定。 執行緒的繼續使用"C"地區設定，因為執行緒 A 已經啟用個別執行緒地區設定中的 C 執行階段程式庫函式。 此外，因為[setlocale](../preprocessor/setlocale.md)不會影響 c + + 標準程式庫地區設定，所有 c + + 標準程式庫物件會繼續使用"C"地區設定。  
  
```  
// multithread_locale_3.cpp  
// compile with: /EHsc /MD  
#include <clocale>  
#include <cstdio>  
#include <locale>  
#include <process.h>  
#include <windows.h>  
  
#define NUM_THREADS 2  
using namespace std;  
  
unsigned __stdcall RunThreadA(void *params);  
unsigned __stdcall RunThreadB(void *params);  
  
BOOL localeSet = FALSE;  
BOOL configThreadLocaleCalled = FALSE;  
HANDLE printMutex = CreateMutex(NULL, FALSE, NULL);  
  
int main()  
{  
    HANDLE threads[NUM_THREADS];  
  
    unsigned aID;  
    threads[0] = (HANDLE)_beginthreadex(  
        NULL, 0, RunThreadA, NULL, 0, &aID);  
  
    unsigned bID;  
    threads[1] = (HANDLE)_beginthreadex(  
        NULL, 0, RunThreadB, NULL, 0, &bID);  
  
    WaitForMultipleObjects(2, threads, TRUE, INFINITE);  
  
    printf_s("[Thread main] Per-thread locale is NOT enabled.\n");  
    printf_s("[Thread main] CRT locale is set to \"%s\"\n",  
        setlocale(LC_ALL, NULL));  
    printf_s("[Thread main] locale::global is set to \"%s\"\n",  
        locale().name().c_str());  
  
    CloseHandle(threads[0]);  
    CloseHandle(threads[1]);  
    CloseHandle(printMutex);  
  
    return 0;  
}  
  
unsigned __stdcall RunThreadA(void *params)  
{  
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);  
    configThreadLocaleCalled = TRUE;  
    while (!localeSet)  
        Sleep(100);  
  
    WaitForSingleObject(printMutex, INFINITE);  
    printf_s("[Thread A] Per-thread locale is enabled.\n");  
    printf_s("[Thread A] CRT locale is set to \"%s\"\n",  
        setlocale(LC_ALL, NULL));  
    printf_s("[Thread A] locale::global is set to \"%s\"\n\n",  
        locale().name().c_str());  
    ReleaseMutex(printMutex);  
  
    return 1;  
}  
  
unsigned __stdcall RunThreadB(void *params)  
{  
    while (!configThreadLocaleCalled)  
        Sleep(100);  
    setlocale(LC_ALL, "french");  
    localeSet = TRUE;  
  
    WaitForSingleObject(printMutex, INFINITE);  
    printf_s("[Thread B] Per-thread locale is NOT enabled.\n");  
    printf_s("[Thread B] CRT locale is set to \"%s\"\n",  
        setlocale(LC_ALL, NULL));  
    printf_s("[Thread B] locale::global is set to \"%s\"\n\n",  
        locale().name().c_str());  
    ReleaseMutex(printMutex);  
  
    return 1;  
}  
```  
  
```Output  
[Thread B] Per-thread locale is NOT enabled.  
[Thread B] CRT locale is set to "French_France.1252"  
[Thread B] locale::global is set to "C"  
  
[Thread A] Per-thread locale is enabled.  
[Thread A] CRT locale is set to "C"  
[Thread A] locale::global is set to "C"  
  
[Thread main] Per-thread locale is NOT enabled.  
[Thread main] CRT locale is set to "French_France.1252"  
[Thread main] locale::global is set to "C"  
```  
  
## <a name="example"></a>範例  
 在此範例中，主執行緒會繁衍兩個子執行緒。 第一個執行緒的執行緒，讓每個執行緒的地區設定，藉由呼叫`_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`。 第二個執行緒、 執行緒 B，以及主執行緒中，請勿啟用個別執行緒地區設定。 執行緒 B，然後繼續進行變更地區設定使用[locale:: global](../standard-library/locale-class.md#global)方法的 c + + 標準程式庫。  
  
 由於執行緒 B 不需要啟用個別執行緒地區設定，主執行緒和執行緒 B 中的 C 執行階段程式庫函式會開始使用 「 法文 」 的地區設定。 執行緒的繼續使用"C"地區設定，因為執行緒 A 已經啟用個別執行緒地區設定中的 C 執行階段程式庫函式。 不過，由於[locale:: global](../standard-library/locale-class.md#global)方法變更地區設定 「 全域 」，則所有的執行緒中所有 c + + 標準程式庫物件可讓您開始使用 「 法文 」 的地區設定。  
  
```  
// multithread_locale_4.cpp  
// compile with: /EHsc /MD  
#include <clocale>  
#include <cstdio>  
#include <locale>  
#include <process.h>  
#include <windows.h>  
  
#define NUM_THREADS 2  
using namespace std;  
  
unsigned __stdcall RunThreadA(void *params);  
unsigned __stdcall RunThreadB(void *params);  
  
BOOL localeSet = FALSE;  
BOOL configThreadLocaleCalled = FALSE;  
HANDLE printMutex = CreateMutex(NULL, FALSE, NULL);  
  
int main()  
{  
    HANDLE threads[NUM_THREADS];  
  
    unsigned aID;  
    threads[0] = (HANDLE)_beginthreadex(  
        NULL, 0, RunThreadA, NULL, 0, &aID);  
  
    unsigned bID;  
    threads[1] = (HANDLE)_beginthreadex(  
        NULL, 0, RunThreadB, NULL, 0, &bID);  
  
    WaitForMultipleObjects(2, threads, TRUE, INFINITE);  
  
    printf_s("[Thread main] Per-thread locale is NOT enabled.\n");  
    printf_s("[Thread main] CRT locale is set to \"%s\"\n",  
        setlocale(LC_ALL, NULL));  
    printf_s("[Thread main] locale::global is set to \"%s\"\n",  
        locale().name().c_str());  
  
    CloseHandle(threads[0]);  
    CloseHandle(threads[1]);  
    CloseHandle(printMutex);  
  
    return 0;  
}  
  
unsigned __stdcall RunThreadA(void *params)  
{  
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);  
    configThreadLocaleCalled = TRUE;  
    while (!localeSet)  
        Sleep(100);  
  
    WaitForSingleObject(printMutex, INFINITE);  
    printf_s("[Thread A] Per-thread locale is enabled.\n");  
    printf_s("[Thread A] CRT locale is set to \"%s\"\n",  
        setlocale(LC_ALL, NULL));  
    printf_s("[Thread A] locale::global is set to \"%s\"\n\n",  
        locale().name().c_str());  
    ReleaseMutex(printMutex);  
  
    return 1;  
}  
  
unsigned __stdcall RunThreadB(void *params)  
{  
    while (!configThreadLocaleCalled)  
        Sleep(100);  
    locale::global(locale("french"));  
    localeSet = TRUE;  
  
    WaitForSingleObject(printMutex, INFINITE);  
    printf_s("[Thread B] Per-thread locale is NOT enabled.\n");  
    printf_s("[Thread B] CRT locale is set to \"%s\"\n",  
        setlocale(LC_ALL, NULL));  
    printf_s("[Thread B] locale::global is set to \"%s\"\n\n",  
        locale().name().c_str());  
    ReleaseMutex(printMutex);  
  
    return 1;  
}  
```  
  
```Output  
[Thread B] Per-thread locale is NOT enabled.  
[Thread B] CRT locale is set to "French_France.1252"  
[Thread B] locale::global is set to "French_France.1252"  
  
[Thread A] Per-thread locale is enabled.  
[Thread A] CRT locale is set to "C"  
[Thread A] locale::global is set to "French_France.1252"  
  
[Thread main] Per-thread locale is NOT enabled.  
[Thread main] CRT locale is set to "French_France.1252"  
[Thread main] locale::global is set to "French_France.1252"  
```  
  
## <a name="see-also"></a>另請參閱  
 [多執行緒支援對舊版程式碼 （Visual c + +）](../parallel/multithreading-support-for-older-code-visual-cpp.md)   
 [_beginthread、_beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)   
 [_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md)   
 [setlocale](../preprocessor/setlocale.md)   
 [國際化](../c-runtime-library/internationalization.md)   
 [地區設定](../c-runtime-library/locale.md)   
 [\<clocale >](../standard-library/clocale.md)   
 [\<locale>](../standard-library/locale.md)   
 [locale 類別](../standard-library/locale-class.md)