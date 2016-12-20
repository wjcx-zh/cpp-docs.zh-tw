---
title: "_configthreadlocale | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_configthreadlocale"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-locale-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_configthreadlocale"
  - "configthreadlocale"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_configthreadlocale 函式"
  - "configthreadlocale 函式"
  - "地區設定, 個別執行緒"
  - "個別執行緒的地區設定"
  - "執行緒的地區設定"
ms.assetid: 10e4050e-b587-4f30-80bc-6c76b35fc770
caps.latest.revision: 24
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _configthreadlocale
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

設定個別執行緒地區設定選項。  
  
## 語法  
  
```  
int _configthreadlocale(  
   int type  
);  
```  
  
#### 參數  
 `type`  
 要設定的選項。  下表所列出的其中一個選項。  
  
## 傳回值  
 上述個別執行緒地區設定狀態 \(`_DISABLE_PER_THREAD_LOCALE` 或 `_ENABLE_PER_THREAD_LOCALE`\)，或者失敗為 \-1 。  
  
## 備註  
 `_configurethreadlocale` 函式用於控制執行緒特定地區設定的用途。  使用其中一個選項指定或判斷個別執行緒地區設定狀態：  
  
 `_ENABLE_PER_THREAD_LOCALE`  
 讓目前的執行緒使用執行緒特定地區設定。  在此執行緒對 `setlocale` 的後續呼叫只會影響執行緒本身的地區設定。  
  
 `_DISABLE_PER_THREAD_LOCALE`  
 讓目前的執行緒使用全域地區設定。  在此執行緒對 `setlocale` 的後續呼叫會影響其他使用全域地區設定的執行緒。  
  
 `0`  
 擷取這個特定執行緒的目前設定。  
  
 這些函式會影響`setlocale`、`_tsetlocale`、`_wsetlocale`、`_beginthread`及 `_beginthreadex`的行為。  如果另一個方法用於建立執行緒，地區設定不會影響其他執行緒。  
  
 在個別執行緒地區設定停用時， `setlocale` 或 `_wsetlocale` 的任何後續呼叫將變更執行緒地區設定。  在個別執行緒地區設定啟動時， `setlocale` 或 `_wsetlocale` 只會影響目前執行緒的地區設定。  
  
 如果您使用 `_configurethreadlocale` 啟用個別執行緒地區設定，建議您隨即呼叫 `setlocale` 或 `_wsetlocale` 設定該執行緒的慣用地區設定。  
  
 如果 `type` 不在表格中列出的任何一值，此函式叫用無效的參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，則此函示設定`errno`為`EINVAL`並回傳\-1。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_configthreadlocale`|\<locale.h\>|  
  
## 範例  
  
```  
// crt_configthreadlocale.cpp  
//   
// This program demonstrates the use of _configthreadlocale when  
// using is two independent threads.  
//  
  
#include <locale.h>  
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
unsigned __stdcall SecondThreadFunc( void* pArguments )  
{  
    unsigned char str[BUFF_SIZE];  
  
    // Set the thread code page  
    _setmbcp(_MB_CP_ANSI)  
  
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
  
    // Configure per-thread locale to cause all subsequently created   
    // threads to have their own locale.  
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
  
  **執行緒地區設定現若設定為 English\_United States.1252。**  
**時間在英語地區設定如下:「Wednesday, May 12, 2004」**  
**執行緒地區設定現若設定為 German\_Germany.1252。**  
**時間在德語地區設定如下:「Mittwoch, 12.  Mai 2004」**    
## .NET Framework 對等用法  
 不適用。不過，請參閱 [使用 CurrentCulture 屬性](http://msdn.microsoft.com/zh-tw/3156042d-6082-4205-90b4-c917ae6a3ba6)。  
  
## 請參閱  
 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [\_beginthread、\_beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [多執行緒和地區設定](../../parallel/multithreading-and-locales.md)