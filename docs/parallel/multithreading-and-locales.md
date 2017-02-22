---
title: "多執行緒和地區設定 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "地區設定 [C++], 多執行緒"
  - "多執行緒 [C++], 地區設定"
  - "個別執行緒的地區設定"
  - "執行緒 [C++], 地區設定"
ms.assetid: d6fb159a-eaca-4130-a51a-f95d62f71485
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 多執行緒和地區設定
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C 執行階段程式庫和 Standard C\+\+ 程式庫都提供變更程式地區設定 \(Locale\) 的支援。  本主題討論在多執行緒應用程式 \(Multithreaded Application\) 中使用這兩個程式庫的地區設定功能時，所引發的問題。  
  
## 備註  
 在 C 執行階段程式庫中，您可以使用 `_beginthread` 和 `_beginthreadex` 函式建立多執行緒應用程式。  這個主題只涵蓋使用這些函式建立的多執行緒應用程式。  如需詳細資訊，請參閱[\_beginthread、\_beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)。  
  
 若要使用 C 執行階段程式庫變更地區設定，請使用 [setlocale](../preprocessor/setlocale.md) 函式。  在舊版 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 中，此函式一定會修改整個應用程式的地區設定，  現在，則支援以個別執行緒為基礎，來設定地區設定。  這是使用 [\_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md) 函式來完成。  若要指定 [setlocale](../preprocessor/setlocale.md) 只能變更目前執行緒中的地區設定，請呼叫該執行緒中的 `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`。  相反地，呼叫 `_configthreadlocale(_DISABLE_PER_THREAD_LOCALE)` 將會造成該執行緒使用全域地區設定，並且該執行緒中任何 [setlocale](../preprocessor/setlocale.md) 的呼叫，都將變更尚未明確啟用個別執行緒地區設定之所有執行緒中的地區設定。  
  
 若要使用 C\+\+ 執行階段程式庫變更地區設定，請使用 [locale 類別](../standard-library/locale-class.md)。  您可以藉由呼叫 [locale::global](../Topic/locale::global.md) 方法，變更尚未明確啟用個別執行緒地區設定之每個執行緒中的地區設定。  若要變更單一執行緒或部分應用程式中的地區設定，只要在該執行緒或程式碼的部分建立 `locale` 物件的執行個體即可。  
  
> [!NOTE]
>  呼叫 [locale::global](../Topic/locale::global.md) 會變更 Standard C\+\+ 程式庫和 C 執行階段程式庫的地區設定。  然而，呼叫 [setlocale](../preprocessor/setlocale.md) 只會變更 C 執行階段程式庫的地區設定，而 Standard C\+\+ 程式庫則不會受到影響。  
  
 下列範例示範如何使用 [setlocale](../preprocessor/setlocale.md) 函式、[locale 類別](../standard-library/locale-class.md) 和 [\_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md) 函式，在數種不同案例中變更應用程式的地區設定。  
  
## 範例  
 在此範例中，主執行緒會繁衍 \(Spawn\) 兩個子執行緒。  第一個執行緒 \(也就是執行緒 A\) 會藉由呼叫 `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)` 以啟用個別執行緒的地區設定。  第二個執行緒 \(也就是執行緒 B\) 以及主執行緒都不會啟用個別執行緒的地區設定。  然後，執行緒 A 會使用 C 執行階段程式庫的 [setlocale](../preprocessor/setlocale.md) 函式繼續變更地區設定。  
  
 由於執行緒 A 已啟用個別執行緒的地區設定，所以只有執行緒 A 中的 C 執行階段程式庫函式會使用「法文」地區設定。  在執行緒 B 和主執行緒中的 C 執行階段程式庫函式會繼續使用 "C" 地區設定。  此外，由於 [setlocale](../preprocessor/setlocale.md) 不會影響 Standard C\+\+ 程式庫的地區設定，因此，所有的 Standard C\+\+ 程式庫物件會繼續使用 "C" 地區設定。  
  
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
  
  **\[執行緒 A\] 個別執行緒地區設定已啟用。**  
**\[執行緒 A\] CRT 地區設定設為「French\_France.1252」**  
**\[執行緒 A\] locale::global 設為「C」**  
**\[執行緒 B\] 個別執行緒地區設定未啟用。**  
**\[執行緒 B\] CRT 地區設定設為「C」**  
**\[執行緒 B\] locale::global 設為「C」**  
**\[主執行緒\] 個別執行緒地區設定未啟用。**  
**\[主執行緒\] CRT 地區設定設為「C」**  
**\[主執行緒\] locale::global 設為「C」**   
## 範例  
 在此範例中，主執行緒會繁衍 \(Spawn\) 兩個子執行緒。  第一個執行緒 \(也就是執行緒 A\) 會藉由呼叫 `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)` 以啟用個別執行緒的地區設定。  第二個執行緒 \(也就是執行緒 B\) 以及主執行緒都不會啟用個別執行緒的地區設定。  然後，執行緒 A 會使用 Standard C\+\+ 程式庫的 [locale::global](../Topic/locale::global.md) 方法繼續變更地區設定。  
  
 由於執行緒 A 已啟用個別執行緒的地區設定，所以只有執行緒 A 中的 C 執行階段程式庫函式會使用「法文」地區設定。  在執行緒 B 和主執行緒中的 C 執行階段程式庫函式會繼續使用 "C" 地區設定。  然而，由於 [locale::global](../Topic/locale::global.md) 方法會全域地變更地區設定，因此，所有執行緒中的所有 Standard C\+\+ 程式庫物件都會啟動使用「法文」地區設定。  
  
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
  
  **\[執行緒 A\] 個別執行緒地區設定已啟用。**  
**\[執行緒 A\] CRT 地區設定設為「French\_France.1252」**  
**\[執行緒 A\] locale::global 設為「French\_France.1252」**  
**\[執行緒 B\] 個別執行緒地區設定未啟用。**  
**\[執行緒 B\] CRT 地區設定設為「C」**  
**\[執行緒 B\] locale::global 設為「French\_France.1252」**  
**\[主執行緒\] 個別執行緒地區設定未啟用。**  
**\[主執行緒\] CRT 地區設定設為「C」**  
**\[主執行緒\] locale::global 設為「French\_France.1252」**   
## 範例  
 在此範例中，主執行緒會繁衍 \(Spawn\) 兩個子執行緒。  第一個執行緒 \(也就是執行緒 A\) 會藉由呼叫 `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)` 以啟用個別執行緒的地區設定。  第二個執行緒 \(也就是執行緒 B\) 以及主執行緒都不會啟用個別執行緒的地區設定。  然後，執行緒 B 會使用 C 執行階段程式庫的 [setlocale](../preprocessor/setlocale.md) 函式繼續變更地區設定。  
  
 由於執行緒 B 尚未啟用個別執行緒的地區設定，因此，執行緒 B 和主執行緒中的 C 執行階段程式庫函式會啟動使用「法文」地區設定。  執行緒 A 中的 C 執行階段程式庫函式會繼續使用 "C" 地區設定，因為執行緒 A 已經啟用個別執行緒的地區設定。  此外，由於 [setlocale](../preprocessor/setlocale.md) 不會影響 Standard C\+\+ 程式庫的地區設定，因此，所有的 Standard C\+\+ 程式庫物件會繼續使用 "C" 地區設定。  
  
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
  
  **\[執行緒 B\] 個別執行緒地區設定未啟用。**  
**\[執行緒 B\] CRT 地區設定設為「French\_France.1252」**  
**\[執行緒 B\] locale::global 設為「C」**  
**\[執行緒 A\] 個別執行緒地區設定已啟用。**  
**\[Thread A\] CRT 地區設定設為「C」**  
**\[執行緒 A\] locale::global 設為「C」**  
**\[主執行緒\] 個別執行緒地區設定未啟用。**  
**\[主執行緒\] CRT 地區設定設為「French\_France.1252」**  
**\[主執行緒\] locale::global 設為「C」**   
## 範例  
 在此範例中，主執行緒會繁衍 \(Spawn\) 兩個子執行緒。  第一個執行緒 \(也就是執行緒 A\) 會藉由呼叫 `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)` 以啟用個別執行緒的地區設定。  第二個執行緒 \(也就是執行緒 B\) 以及主執行緒都不會啟用個別執行緒的地區設定。  然後，執行緒 B 會使用 Standard C\+\+ 程式庫的 [locale::global](../Topic/locale::global.md) 方法繼續變更地區設定。  
  
 由於執行緒 B 尚未啟用個別執行緒的地區設定，因此，執行緒 B 和主執行緒中的 C 執行階段程式庫函式會啟動使用「法文」地區設定。  執行緒 A 中的 C 執行階段程式庫函式會繼續使用 "C" 地區設定，因為執行緒 A 已經啟用個別執行緒的地區設定。  然而，由於 [locale::global](../Topic/locale::global.md) 方法會全域地變更地區設定，因此，所有執行緒中的所有 Standard C\+\+ 程式庫物件都會啟動使用「法文」地區設定。  
  
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
  
  **\[執行緒 B\] 個別執行緒地區設定未啟用。**  
**\[執行緒 B\] CRT 地區設定設為「French\_France.1252」**  
**\[執行緒 B\] locale::global 設為「French\_France.1252」**  
**\[執行緒 A\] 個別執行緒地區設定已啟用。**  
**\[Thread A\] CRT 地區設定設為「C」**  
**\[執行緒 A\] locale::global 設為「French\_France.1252」**  
**\[主執行緒\] 個別執行緒地區設定未啟用。**  
**\[主執行緒\] CRT 地區設定設為「French\_France.1252」**  
**\[主執行緒\] locale::global 設為「French\_France.1252」**   
## 請參閱  
 [舊版程式碼的多執行緒支援 \(Visual C\+\+\)](../parallel/multithreading-support-for-older-code-visual-cpp.md)   
 [\_beginthread、\_beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)   
 [\_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md)   
 [setlocale](../preprocessor/setlocale.md)   
 [國際化](../c-runtime-library/internationalization.md)   
 [地區設定](../c-runtime-library/locale.md)   
 [\<clocale\>](../standard-library/clocale.md)   
 [\<locale\>](../standard-library/locale.md)   
 [locale 類別](../standard-library/locale-class.md)