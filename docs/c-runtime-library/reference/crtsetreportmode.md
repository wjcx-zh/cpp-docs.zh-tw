---
title: "_CrtSetReportMode | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CrtSetReportMode"
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
  - "_CrtSetReportMode"
  - "CrtSetReportMode"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_CrtSetReportMode 函式"
  - "CrtSetReportMode 函式"
ms.assetid: 3ecc6a12-afdd-4242-b046-8187ff6d4b36
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# _CrtSetReportMode
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

被 `_CrtDbgReport` 和任何巨集呼叫 [\_CrtDbgReport、\_CrtDbgReportW](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md), 像是 [\_ASSERT、\_ASSERTE、\_ASSERT\_EXPR 巨集](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md), [\_ASSERT、\_ASSERTE、\_ASSERT\_EXPR 巨集](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md), [\_RPT、\_RPTF、\_RPTW、\_RPTFW 巨集](../../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md) 和 [\_RPT、\_RPTF、\_RPTW、\_RPTFW 巨集](../../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md) \(僅偵錯版本\) 指定目的地或特定報表類型的目的地。  
  
## 語法  
  
```  
int _CrtSetReportMode(   
   int reportType,  
   int reportMode   
);  
```  
  
#### 參數  
 `reportType`  
 報告類型: `_CRT_WARN`、 `_CRT_ERROR`、和`_CRT_ASSERT`。  
  
 `reportMode`  
 新的報表模式或 `reportType` 的模式。  
  
## 傳回值  
 在成功完成時， `reportType`傳回之前報表模式或模式由`_CrtSetReportMode` 所針對的報表類型。  如果傳遞當 `reportType` 或 `reportMode`中一個無效的模式時為 ， `_CrtSetReportMode` 叫用無效的參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，則此函示設定`errno`為`EINVAL`並回傳\-1。  如需詳細資訊，請參閱[errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 `_CrtSetReportMode` 為 `_CrtDbgReport`指定輸出目標。  由於巨集 `_ASSERT`、 `_ASSERTE`、 `_RPT`和 `_RPTF` 呼叫 `_CrtDbgReport`，則 `_CrtSetReportMode` 會指定文字輸出目標指定與這些巨集。  
  
 如果未定義 [\_DEBUG](../../c-runtime-library/debug.md)，在前置處理中，對 `_CrtSetReportMode` 的呼叫將被移除。  
  
 如果您不呼叫 `_CrtSetReportMode` 定義訊息的輸出目標，則下列預設實際上是:  
  
-   判斷提示失敗和錯誤導向至偵錯訊息視窗。  
  
-   從 Windows 應用程式的警告會發出到偵錯工具的輸出視窗。  
  
-   從主控台應用程式的警告不會顯示。  
  
 下表列出 Crtdbg.h 定義的報告類型。  
  
|回報類型|描述|  
|----------|--------|  
|`_CRT_WARN`|警告、訊息和不需要直接顧慮的資訊。|  
|`_CRT_ERROR`|錯誤、不可復原之問題和無法直接注意的議題。|  
|`_CRT_ASSERT`|判斷提示失敗 \(評估為 `FALSE` 的運算式\) 。|  
  
 `_CrtSetReportMode` 函式會在 `reportMode` 指定的新報告方式對 `reportType` 中指定的報告類型並傳回 `reportType`的先前定義的報表模式。  下表列出 `reportMode` 的可用選項和 `_CrtDbgReport`發生的行為。  這些選項做為位元旗標在 Crtdbg.h 中定義。  
  
|報表模式|\_CrtDbgReport 的行為|  
|----------|------------------------|  
|`_CRTDBG_MODE_DEBUG`|將訊息寫入至偵錯工具的輸出視窗。|  
|`_CRTDBG_MODE_FILE`|為使用者提供的檔案控制代碼寫入訊息。  應該呼叫[\_CrtSetReportFile](../../c-runtime-library/reference/crtsetreportfile.md) 定義特定檔案或資料流做為目的端。|  
|`_CRTDBG_MODE_WNDW`|建立訊息方塊與 `Abort`、 `Retry`和 `Ignore` 按鈕時顯示訊息。|  
|`_CRTDBG_REPORT_MODE`|傳回 `reportMode` 指定的 `reportType`。<br /><br /> 1   `_CRTDBG_MODE_FILE`<br /><br /> 2   `_CRTDBG_MODE_DEBUG`<br /><br /> 4   `_CRTDBG_MODE_WNDW`|  
  
 每個報告類型可以報告使用中的是一個，兩個或三個或沒有任何模式。  因此，可能會有一個以上的單一報告類型定義的目的地。  例如，下列程式碼片段會造成判斷提示失敗都會傳送至偵錯訊息視窗和新增至 `stderr`:  
  
```  
_CrtSetReportMode( _CRT_ASSERT, _CRTDBG_MODE_FILE | _CRTDBG_MODE_WNDW );  
_CrtSetReportFile( _CRT_ASSERT, _CRTDBG_FILE_STDERR );  
```  
  
 此外，報告方式或方式每個報告型別可以單獨控制。  例如，指定可能的 `_CRT_WARN` `reportType` 傳送至輸出偵錯，字串，而 `_CRT_ASSERT` 顯示使用偵錯訊息視窗並傳送至 `stderr`，如先前所述。  
  
## 需求  
  
|常式|必要的標頭|選擇性標頭|  
|--------|-----------|-----------|  
|`_CrtSetReportMode`|\<crtdbg.h\>|\<errno.h\>|  
  
 如需詳細資訊，請參閱介紹中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
 **程式庫：** 僅 [CRT 程式庫功能](../../c-runtime-library/crt-library-features.md) 之偵錯版本。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)