---
title: "_putenv、_wputenv | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_putenv"
  - "_wputenv"
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
  - "api-ms-win-crt-environment-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_tputenv"
  - "_wputenv"
  - "_putenv"
  - "wputenv"
  - "tputenv"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_putenv 函式"
  - "_tputenv 函式"
  - "_wputenv 函式"
  - "環境變數, 建立"
  - "環境變數, 刪除"
  - "環境變數, 修改"
  - "putenv 函式"
  - "tputenv 函式"
  - "wputenv 函式"
ms.assetid: 9ba9b7fd-276e-45df-8420-d70c4204b8bd
caps.latest.revision: 22
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _putenv、_wputenv
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

建立、修改，或移除環境變數。  更多這些函式的可用安全版本，請參閱 [\_putenv\_s、\_wputenv\_s](../../c-runtime-library/reference/putenv-s-wputenv-s.md)。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
int _putenv(  
   const char *envstring   
);  
int _wputenv(  
   const wchar_t *envstring   
);  
```  
  
#### 參數  
 `envstring`  
 環境字串定義。  
  
## 傳回值  
 如果成功則回傳 0，如果是錯誤情況則回傳 \-1。  
  
## 備註  
 `_putenv` 函式會將新的環境變數或修改現有的環境變數的值。  環境變數定義執行流程的環境 \(例如，程式可以連結到為了文件庫所設的預設路徑\)。  `_wputenv` 是 `_putenv` 的寬字元版本。 `_wputenv` 的 `envstring` 引數是寬字元字串。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE and \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|------------------------------|----------------|-------------------|  
|`_tputenv`|`_putenv`|`_putenv`|`_wputenv`|  
  
 `envstring` 引數必須是指標到表單 `varname=string`的字串， `varname` 是會被增加或修改的環境變數而 `string` 是變數值。  如果 `varname` 已經是環境的一部分，它的值會由 `string`取代; 否則，新 `varname` 變數和其 `string` 值會被加入至環境。  您可以藉由指定空的`string`以移除環境變數，換句話說，您可以僅指定 `varname=` 以完成移除環境變數。  
  
 `_putenv` 和 `_wputenv` 只會影響目前處理序的環境; 您不能使用這些修改命令層級環境。  也就是這些函式只能在資料結構供執行階段文件庫使用而不是為了利用作業系統在環境區塊建立處理流程。  當目前的處理程序終止時，環境會還原至呼叫程序層級 \(多數情況下，都是還原到作業系統層級\)。  不過，修改過的環境可以透過 `_spawn`、 `_exec`或 `system` 傳遞至任何建立的新處理序，因此，這些處理序透過 `_putenv` 和 `_wputenv` 取得任何新項目。  
  
 請勿直接變更環境輸入: 相反地，請使用 `_putenv` 或 `_wputenv` 以變更它。  特別是，直接釋放 `_environ[]` 全域陣列的項目可能會導致無效的記憶體被定址。  
  
 `getenv` 和 `_putenv` 使用這個全域變數 `_environ` 以存取環境表; `_wgetenv` 和 `_wputenv` 使用 `_wenviron`。  `_putenv` 和 `_wputenv` 可能變更 `_environ` 和 `_wenviron`的值，因此無法使用 `_envp` 引數為 `main` 、和`wenvp` 引數為 `wmain`。  因此，使用 `_environ` 或 `_wenviron` 存取環境資訊比較安全。  如需 `_putenv` 和 `_wputenv` 的關聯性的詳細資訊與全域變數，請參閱 [\_environ， \_wenviron](../../c-runtime-library/environ-wenviron.md)。  
  
> [!NOTE]
>  `_putenv` 和 `_getenv` 函式群不是安全執行緒。  當 `_putenv` 修改字串時產生隨機失敗，`_getenv` 會傳回字串指標。  確定這些函式的呼叫已同步。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_putenv`|\<stdlib.h\>|  
|`_wputenv`|\<stdlib.h\> 或 \<wchar.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
 如需使用 `_putenv` 的範例，請參閱[getenv、\_wgetenv](../../c-runtime-library/reference/getenv-wgetenv.md)。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)   
 [getenv、\_wgetenv](../../c-runtime-library/reference/getenv-wgetenv.md)   
 [\_searchenv、\_wsearchenv](../../c-runtime-library/reference/searchenv-wsearchenv.md)