---
title: "_CrtSetReportHook2、_CrtSetReportHookW2 | Microsoft Docs"
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
  - "_CrtSetReportHook2"
  - "_CrtSetReportHookW2"
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
apitype: "DLLExport"
f1_keywords: 
  - "CrtSetReportHookW2"
  - "CrtSetReportHook2"
  - "_CrtSetReportHookW2"
  - "_CrtSetReportHook2"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "CrtSetReportHook2 函式"
  - "_CrtSetReportHook2 函式"
  - "_CrtSetReportHookW2 函式"
  - "CrtSetReportHookW2 函式"
ms.assetid: 12e5f68d-c8a7-4b1a-9a75-72ba4a8592d0
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _CrtSetReportHook2、_CrtSetReportHookW2
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

您可以安裝或移除一個客戶定義報告函示，藉由將它安裝在 C 執行時間偵錯報告階段 \(僅偵錯版本\) 上。  
  
## 語法  
  
```  
  
      int _CrtSetReportHook2(  
   int mode,  
   _CRT_REPORT_HOOK pfnNewHook  
);  
int _CrtSetReportHookW2(  
   int mode,  
   _CRT_REPORT_HOOKW pfnNewHook  
);  
```  
  
#### 參數  
 `mode`  
 要採取的動作：`_CRT_RPTHOOK_INSTALL` 或 `_CRT_RPTHOOK_REMOVE`。  
  
 `pfnNewHook`  
 報告攔截安裝或移除此函式窄字元版本。  
  
 `pfnNewHook`  
 報告攔截安裝或移除此函式寬字元版本。  
  
## 傳回值  
 如果發生錯誤為 \-1，與 `EINVAL` 或 `ENOMEM` 設定；否則在呼叫之後傳回參考 `pfnNewHook` 的計數。  
  
## 備註  
 `_CrtSetReportHook2` 和 `_CrtSetReportHookW2`  可讓您安裝或解除包裝函式，而 [\_CrtSetReportHook](../../c-runtime-library/reference/crtsetreporthook.md) 只讓您攔截函式。  
  
 應該使用`_CrtSetReportHook2` 或 `_CrtSetReportHookW2` 而非 `_CrtSetReportHook` ，當攔截呼叫在 DLL 時呼叫，而且當多個 DLL 可能是載入和設定自己的攔截函式。  在這種情況下，DLL 可以按照不同的順序進行解除安裝比它們載入並攔截函式，可以卸載 DLL。  如果攔截函式加入與 `_CrtSetReportHook` 一起，任何偵錯輸出損毀處理序。  
  
 如果沒有攔截函式具有 `_CrtSetReportHook2` 或 `_CrtSetReportHookW2` ，所有攔截函式會呼叫 `_CrtSetReportHook` ，或者如果所有攔截函式具有 `_CrtSetReportHook2` 和 `_CrtSetReportHookW2` 會傳回 `FALSE`。  
  
 這個函式的寬字元版本可用。  報告攔截函式採用型別的字串 \(寬度或窄字元\) 必須符合所使用之函式的版本。  為報告攔截使用下列函式原型搭配此函式寬字元版本：  
  
```  
int YourReportHook( int reportType, wchar_t *message, int *returnValue );  
```  
  
 為窄字元報告攔截使用下列原型：  
  
```  
int YourReportHook( int reportType, char *message, int *returnValue );  
```  
  
 這些函式會驗證它們的參數。  如果 `mode` 或 `pfnNewNook` 是無效的，則這些函示叫用無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，這些函式會將 `errno` 設為 `EINVAL`，並傳回 \-1。  
  
> [!NOTE]
>  如果您的應用程式是 `/clr` 編譯的，並在應用程式結束主要函式之後回報函式呼叫， CLR 將會擲回例外狀況，如果報告函式呼叫任何 CRT 函式。  
  
## 需求  
  
|常式|必要的標頭|選擇性標頭|  
|--------|-----------|-----------|  
|`_CrtSetReportHook2`|\<crtdbg.h\>|\<errno.h\>|  
|`_CrtSetReportHookW2`|\<crtdbg.h\>|\<errno.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 程式庫  
 [C run\-time libraries](../../c-runtime-library/crt-library-features.md) 版本的偵錯  
  
## 範例  
  
```  
// crt_setreporthook2.c  
#include <windows.h>  
#include <stdio.h>  
#include <crtdbg.h>  
#include <assert.h>  
  
int __cdecl TestHook1(int nReportType, char* szMsg, int* pnRet)  
{  
   int nRet = FALSE;  
  
   printf("CRT report hook 1.\n");  
   printf("CRT report type is \"");  
   switch (nReportType)  
   {  
      case _CRT_ASSERT:  
      {  
         printf("_CRT_ASSERT");  
         // nRet = TRUE;   // Always stop for this type of report  
         break;  
      }  
  
      case _CRT_WARN:  
      {  
         printf("_CRT_WARN");  
         break;  
      }  
  
      case _CRT_ERROR:  
      {  
         printf("_CRT_ERROR");  
         break;  
      }  
  
      default:  
      {  
         printf("???Unknown???");  
         break;  
      }  
   }  
  
   printf("\".\nCRT report message is:\n\t");  
   printf(szMsg);  
  
   if   (pnRet)  
      *pnRet = 0;  
  
   return   nRet;  
}  
  
int __cdecl   TestHook2(int nReportType, char* szMsg, int* pnRet)  
{  
   int   nRet = FALSE;  
  
   printf("CRT report hook 2.\n");  
   printf("CRT report type is \"");  
   switch   (nReportType)  
   {  
      case _CRT_WARN:  
      {  
         printf("_CRT_WARN");  
         break;  
      }  
  
      case _CRT_ERROR:  
      {  
         printf("_CRT_ERROR");  
         break;  
      }  
  
      case _CRT_ASSERT:  
      {  
         printf("_CRT_ASSERT");  
         nRet = TRUE;   // Always stop for this type of report  
         break;  
      }  
  
      default:  
      {  
         printf("???Unknown???");  
         break;  
      }  
   }  
  
   printf("\".\nCRT report message is: \t");  
   printf(szMsg);  
  
   if   (pnRet)  
      *pnRet = 0;  
   // printf("CRT report code is %d.\n", *pnRet);  
   return   nRet;  
}  
  
int   main(int argc, char* argv[])  
{  
   int   nRet = 0;  
  
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook1);  
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook1)"  
          " returned %d\n", nRet);  
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook2);  
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook2)"  
          " returned %d\n", nRet);  
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook2);  
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook2)"  
          " returned %d\n", nRet);  
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook1);  
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook1)"  
          " returned %d\n", nRet);  
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook1);  
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook1)"  
          " returned %d\n", nRet);  
  
   _ASSERT(0);  
  
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2);  
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2)"  
          " returned %d\n", nRet);  
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2);  
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2)"  
          " returned %d\n", nRet);  
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2);  
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2)"  
          " returned %d\n", nRet);  
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook1);  
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook1)"  
          " returned %d\n", nRet);  
  
   return   nRet;  
}  
```  
  
## Output  
  
```  
_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook1) returned 0  
_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook2) returned 0  
_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook2) returned 0  
_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook1) returned 0  
_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook1) returned 0  
_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2) returned 0  
_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2) returned 0  
_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2) returned 0  
_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook1) returned 0  
```  
  
## 請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)