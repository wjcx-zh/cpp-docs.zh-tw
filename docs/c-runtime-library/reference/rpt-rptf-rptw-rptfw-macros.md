---
title: "_RPT、_RPTF、_RPTW、_RPTFW 巨集 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
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
  - "RPT3"
  - "RPTF4"
  - "_RPT4"
  - "RPT1"
  - "_RPTF0"
  - "RPTF3"
  - "_RPTF4"
  - "RPTF1"
  - "RPT4"
  - "_RPT1"
  - "_RPT0"
  - "RPT0"
  - "_RPTF2"
  - "RPTF0"
  - "_RPT3"
  - "_RPT2"
  - "_RPTF3"
  - "RPT2"
  - "_RPTF1"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "偵錯 [CRT], 使用巨集"
  - "_RPTW3 巨集"
  - "_RPT0 巨集"
  - "RPTW4 巨集"
  - "_RPTF3 巨集"
  - "_RPTW4 巨集"
  - "RPTF4 巨集"
  - "RPTFW2 巨集"
  - "RPTW 巨集"
  - "RPT1 巨集"
  - "_RPTF 巨集"
  - "RPTFW3 巨集"
  - "_RPTW0 巨集"
  - "_RPTF0 巨集"
  - "巨集, 偵錯工具"
  - "_RPTW2 巨集"
  - "RPTF3 巨集"
  - "RPT3 巨集"
  - "RPT0 巨集"
  - "_RPT 巨集"
  - "RPTW3 巨集"
  - "_RPTFW 巨集"
  - "偵錯報告巨集"
  - "RPTF 巨集"
  - "RPT 巨集"
  - "_RPTW 巨集"
  - "RPTF2 巨集"
  - "_RPTF1 巨集"
  - "_RPT1 巨集"
  - "_RPT4 巨集"
  - "_RPTFW2 巨集"
  - "_RPTFW1 巨集"
  - "RPTF0 巨集"
  - "_RPT2 巨集"
  - "RPTFW 巨集"
  - "_RPTW1 巨集"
  - "_RPTFW0 巨集"
  - "RPT4 巨集"
  - "_RPT3 巨集"
  - "_RPTFW3 巨集"
  - "_RPTF4 巨集"
  - "_RPTFW4 巨集"
  - "_RPTF2 巨集"
  - "RPTW0 巨集"
  - "RPTFW4 巨集"
  - "RPTFW0 巨集"
  - "RPTW2 巨集"
  - "RPTF1 巨集"
  - "RPT2 巨集"
  - "RPTFW1 巨集"
  - "RPTW1 巨集"
ms.assetid: a5bf8b30-57f7-4971-8030-e773b7a1ae13
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# _RPT、_RPTF、_RPTW、_RPTFW 巨集
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

藉由產生偵錯報告追蹤應用程式的進度 \(僅偵錯版本\)。  請注意在 *n* `args` 指定引數的數目，而且可以是 0， 1， 2， 3， 4 或 5。  
  
## 語法  
  
```  
  
      _RPT  
      n  
      (  
   reportType,  
   format,  
...[args]  
);  
_RPTFn(  
   reportType,  
   format,  
   [args]  
);  
_RPTWn(  
   reportType,  
   format   
   [args]  
);  
_RPTFWn(  
   reportType,  
   format   
   [args]  
);  
```  
  
#### 參數  
 `reportType`  
 報告類型: `_CRT_WARN`、 `_CRT_ERROR`或 `_CRT_ASSERT`。  
  
 `format`  
 對產生使用者信息的格式控制字串。  
  
 `args`  
 `format`使用的替換引數。  
  
## 備註  
 這些巨集採用 `reportType`和 `format`參數。  此外，它們可能也會使用四個其他引數，表示由數字附加至巨集名稱。  例如， `_RPT0` 和 `_RPTF0` 不接受其他引數，則為 `_RPT1` ，且 `_RPTF1` 使用 `arg1`， `_RPT2` ， `_RPTF2` 會使用 `arg1` 和 `arg2`，依此類推。  
  
 因為它們可以用來在偵錯期間，追蹤應用程式的進度 `_RPT` 和 `_RPTF` 巨集類似 [printf](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) 函式。  不過，因為它們在應用程式的零售版本中，在 `#ifdef` 陳述式會不需要將避免呼叫這些巨集比 `printf` 更具彈性。  使用 [\_DEBUG](../../c-runtime-library/debug.md) 巨集，這種彈性達成;，當 `_DEBUG` 旗標後， `_RPT` 和 `_RPTF` 巨集才可以使用。  當 `_DEBUG` 沒有定義時，在前置處理中，這些巨集的呼叫將被移除。  
  
 `_RPTW` 和 `_RPTFW` 巨集是這些巨集寬字元版本。  它們是與 `wprintf` 並採取寬字元字串做為引數。  
  
 `_RPT` 巨集呼叫 [\_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) 函式以產生與使用者訊息的偵錯報告。  `_RPTW` 巨集呼叫 `_CrtDbgReportW` 函式產生與寬字元的相同的報表。  除了使用者訊息之外， `_RPTF` 和 `_RPTFW` 巨集建立與報告巨集呼叫的原始程式檔和行號的偵錯報告。  使用者訊息傳遞替代 `arg`\[*n*\] 引數建立輸入 `format` 字串，使用 [printf](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) 函式定義的相同規則。  
  
 `_CrtDbgReport` 或 `_CrtDbgReportW` 產生偵錯報告並決定根據目前報表模式和檔案其目的定義為 `reportType`。  [\_CrtSetReportMode](../../c-runtime-library/reference/crtsetreportmode.md) 和 [\_CrtSetReportFile](../../c-runtime-library/reference/crtsetreportfile.md) 函式定義每個報告類型的目的地。  
  
 如果 `_RPT` 巨集呼叫，且 `_CrtSetReportMode` 和 `_CrtSetReportFile` 未呼叫，訊息會如下所示。  
  
|回報類型|輸出目標|  
|----------|----------|  
|`_CRT_WARN`|警告文字不會顯示。|  
|`_CRT_ERROR`|快顯視窗。  同樣地，如果指定的 `_CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_WNDW);` 。|  
|`_CRT_ASSERT`|與 `_CRT_ERROR` 相同。|  
  
 在 Just\-In\-Time \(JIT\) 偵錯已啟用條件下，當目的是偵錯訊息視窗，而且使用者按一下 **重試** 按鈕時， `_CrtDbgReport` 或 `_CrtDbgReportW` 會傳回 1，讓這些巨集啟動偵錯工具。  如需使用這些巨集的詳細資訊做為偵錯和錯誤處理機制，請參閱 [使用驗證和報告的巨集](../Topic/Macros%20for%20Reporting.md)。  
  
 產生偵錯報告的其他兩個巨集存在。  [\_ASSERT](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) 巨集產生報告，不過，只有在其運算式引數評估為 false。  [\_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) 是就像 `_ASSERT`，不過，包括失敗的運算式在產生的報告。  
  
## 需求  
  
|巨集|必要的標頭|  
|--------|-----------|  
|`_RPT`巨集|\<crtdbg.h\>|  
|`_RPTF`巨集|\<crtdbg.h\>|  
|`_RPTW`巨集|\<crtdbg.h\>|  
|`_RPTFW`巨集|\<crtdbg.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 程式庫  
 [C run\-time libraries](../../c-runtime-library/crt-library-features.md) 版本的偵錯  
  
 雖然同樣為巨集且都因為包含 Crtdbg.h 而加入，應用程式必須連結至偵錯程式庫，因為這些巨集呼叫其他執行階段函式。  
  
## 範例  
 請參閱 [\_ASSERT](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) 主題的範例。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)