---
title: "錯誤處理 (CRT) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.errors"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "錯誤處理, 的 C 常式"
  - "錯誤處理, 程式庫常式"
  - "邏輯錯誤"
  - "測試, 的程式錯誤"
ms.assetid: 125ac697-9eb0-4152-a440-b7842f23d97f
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 錯誤處理 (CRT)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用這些常式處理程式錯誤。  
  
### 錯誤處理常式  
  
|常式|用法|.NET Framework 對等用法|  
|--------|--------|-------------------------|  
|[assert](../c-runtime-library/reference/assert-macro-assert-wassert.md) 巨集|程式設計邏輯錯誤的測試；執行階段程式庫的版本和偵錯版本皆可取得。|[\<caps:sentence id\="tgt8" sentenceid\="14fd9bf776829d73028df00162f7533f" class\="tgtSentence"\>System::Diagnostics::Debug::Assert\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.assert.aspx)|  
|[\_ASSERT, \_ASSERTE](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) 巨集|與 `assert`類似，不過，只有執行階段程式庫的偵錯版本|[\<caps:sentence id\="tgt11" sentenceid\="14fd9bf776829d73028df00162f7533f" class\="tgtSentence"\>System::Diagnostics::Debug::Assert\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.assert.aspx)|  
|[clearerr](../c-runtime-library/reference/clearerr.md)|重設錯誤指示器。  呼叫 `rewind` 或關閉資料流或重設錯誤指示器。|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_eof](../c-runtime-library/reference/eof.md)|檢查在低階 I\/O 的檔案結尾|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[feof](../c-runtime-library/reference/feof.md)|測試檔案結尾。  當`_read` 傳回 0 時，檔案結尾也會指出。|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[ferror](../c-runtime-library/reference/ferror.md)|資料流 I\/O 錯誤的測試|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_RPT, \_RPTF](../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md) 巨集|產生報告類似於 `printf`，不過，只有執行階段程式庫的偵錯版本|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_set\_error\_mode](../c-runtime-library/reference/set-error-mode.md)|修改 `__error_mode` 判斷 C 執行階段位可能造成程式結束的錯誤寫入錯誤訊息的非預設的位置。||  
|[\_set\_purecall\_handler](../c-runtime-library/reference/get-purecall-handler-set-purecall-handler.md)|為純虛擬函式呼叫設定處理常式。||  
  
## 請參閱  
 [依分類區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)