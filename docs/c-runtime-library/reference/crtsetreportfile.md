---
title: "_CrtSetReportFile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CrtSetReportFile"
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
  - "CrtSetReportFile"
  - "_CrtSetReportFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CrtSetReportFile 函式"
  - "_CrtSetReportFile 函式"
ms.assetid: 3126537e-511b-44af-9c1c-0605265eabc4
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# _CrtSetReportFile
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在您使用 [\_CrtSetReportMode](../../c-runtime-library/reference/crtsetreportmode.md) 指定 `_CRTDBG_MODE_FILE`後，您可以指定檔案控制代碼收到訊息文字。   [\_CrtDbgReport、\_CrtDbgReportW](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) 也使用於`_CrtSetReportFile` 來指定文字的目的端 \(僅偵錯版本\)。  
  
## 語法  
  
```  
_HFILE _CrtSetReportFile(   
   int reportType,  
   _HFILE reportFile   
);  
```  
  
#### 參數  
 `reportType`  
 報告類型: `_CRT_WARN`、 `_CRT_ERROR`、和`_CRT_ASSERT`。  
  
 `reportFile`  
 `reportType`的新報告檔。  
  
## 傳回值  
 在成功完成時，`_CrtSetReportFile` 會傳回指定在 `reportType` 中報告型別定義的上一個報告檔。  如果無效值為 `reportType` 所傳遞，這個函式叫用無效的參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，`errno` 會設定為 `EINVAL` 且函式會傳回 `_CRTDBG_HFILE_ERROR`。  如需詳細資訊，請參閱[errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 `_CrtSetReportFile` 用來以 [\_CrtSetReportMode](../../c-runtime-library/reference/crtsetreportmode.md) 函式定義目的或目的 `_CrtDbgReport` 產生的特定報告型別。  當 `_CrtSetReportMode` 呼叫指派報告的 `_CRTDBG_MODE_FILE` 特定報告型別的方式時，應該呼叫 `_CrtSetReportFile` 所定義的特定檔案或資料流做為目的端。  如果未定義 [\_DEBUG](../../c-runtime-library/debug.md)，在前置處理中，對 `_CrtSetReportFile` 的呼叫將被移除。  
  
 下表顯示 `reportFile` 的可用選項表單和 `_CrtDbgReport`發生的行為。  這些選項定義為在 Crtdbg.h 中的位元旗標。  
  
 `file handle`  
 訊息目標檔案的控制代碼。  已嘗試驗證控制代碼的有效性。  您必須開啟和關閉檔案控制代碼。  例如：  
  
```  
HANDLE hLogFile;  
hLogFile = CreateFile("c:\\log.txt", GENERIC_WRITE,   
   FILE_SHARE_WRITE, NULL, CREATE_ALWAYS,   
   FILE_ATTRIBUTE_NORMAL, NULL);  
_CrtSetReportMode(_CRT_WARN, _CRTDBG_MODE_FILE);  
_CrtSetReportFile(_CRT_WARN, hLogFile);  
  
_RPT0(_CRT_WARN,"file message\n");  
CloseHandle(hLogFile);  
```  
  
 `_CRTDBG_FILE_STDERR`  
 將訊息寫入 `stderr`，可以重新導向如下:  
  
```  
freopen( "c:\\log2.txt", "w", stderr);  
_CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_FILE);  
_CrtSetReportFile(_CRT_ERROR, _CRTDBG_FILE_STDERR);  
  
_RPT0(_CRT_ERROR,"1st message\n");  
```  
  
 `_CRTDBG_FILE_STDOUT`  
 將訊息寫入 `stdout`，您可以重新導向。  
  
 `_CRTDBG_REPORT_FILE`  
 傳回目前的報告模式。  
  
 每個報表型別使用的報告檔可以單獨控制。  例如，指定可能的 `_CRT_ERROR` `reportType` 向 `stderr`報告功能，則為 `_CRT_ASSERT` ，而 `reportType` 向使用者自訂的檔案控制代碼或資料流中會報告。  
  
## 需求  
  
|常式|必要的標頭|選擇性標頭|  
|--------|-----------|-----------|  
|`_CrtSetReportFile`|\<crtdbg.h\>|\<errno.h\>|  
  
 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式不支援主控台。  與主控台關聯的標準資料流控制代碼 \(`stdin`、`stdout` 和 `stderr`\) 必須重新導向，然後 C 執行階段函式才能在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式中使用它們。  如需詳細的相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
 **程式庫：** 僅 [CRT 程式庫功能](../../c-runtime-library/crt-library-features.md) 之偵錯版本。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)