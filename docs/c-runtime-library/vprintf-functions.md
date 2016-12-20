---
title: "vprintf 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcr110.dll"
  - "msvcr120.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr80.dll"
apitype: "DLLExport"
f1_keywords: 
  - "vprintf"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "格式化的文字 [C++]"
  - "vprintf 函式"
ms.assetid: 02ac7c51-eab1-4bf0-bf4c-77065e3fa744
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# vprintf 函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

每個 `vprintf` 函式接收一個指向參數列的指標，然後格式化並將給予的資料寫到目標。  這些函式有參數驗證方式，指示函式接收寬字元或單一位元組字元的字串，輸出目的，和在格式字串中支援規定參數的使用順序等不同。  
  
|||  
|-|-|  
|[\_vcprintf 、 \_vcwprintf](../c-runtime-library/reference/vcprintf-vcprintf-l-vcwprintf-vcwprintf-l.md)|[vfprintf 、 vfwprintf](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|  
|[\_vfprintf\_p、\_vfprintf\_p\_l、\_vfwprintf\_p、\_vfwprintf\_p\_l](../c-runtime-library/reference/vfprintf-p-vfprintf-p-l-vfwprintf-p-vfwprintf-p-l.md)|[vfprintf\_s、\_vfprintf\_s\_l、vfwprintf\_s、\_vfwprintf\_s\_l](../c-runtime-library/reference/vfprintf-s-vfprintf-s-l-vfwprintf-s-vfwprintf-s-l.md)|  
|[vprintf 、 vwprintf](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)|[\_vprintf\_p、\_vprintf\_p\_l、\_vwprintf\_p、\_vwprintf\_p\_l](../c-runtime-library/reference/vprintf-p-vprintf-p-l-vwprintf-p-vwprintf-p-l.md)|  
|[vprintf\_s、\_vprintf\_s\_l、vwprintf\_s、\_vwprintf\_s\_l](../c-runtime-library/reference/vprintf-s-vprintf-s-l-vwprintf-s-vwprintf-s-l.md)|[vsprintf 、 vswprintf](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md)|  
|[\_vsprintf\_p、\_vsprintf\_p\_l、\_vswprintf\_p、\_vswprintf\_p\_l](../c-runtime-library/reference/vsprintf-p-vsprintf-p-l-vswprintf-p-vswprintf-p-l.md)|[vsprintf\_s、\_vsprintf\_s\_l、vswprintf\_s、\_vswprintf\_s\_l](../c-runtime-library/reference/vsprintf-s-vsprintf-s-l-vswprintf-s-vswprintf-s-l.md)|  
|[\_vscprintf、\_vscprintf\_l、\_vscwprintf、\_vscwprintf\_l](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|[\_vsnprintf 、 \_vsnwprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md)|  
  
## 備註  
 `vprintf` 這些函式和下表它們相對的函式相似。  不過，每個 `vprintf` 函式接受的是指向參數列的指標，而它們相對的函式則是接受參數列。  
  
 這些函式為輸出至目標，如下地格式化資料。  
  
|Function|對應函式|輸出目標|參數驗證|位置參數支援|  
|--------------|----------|----------|----------|------------|  
|`_vcprintf`|[\_cprintf](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)|主控台|檢查是否為 null 。|no|  
|`_vcwprintf`|[\_cwprintf](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)|主控台|檢查是否為 null 。|no|  
|`vfprintf`|[fprintf](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|*資料流*|檢查是否為 null 。|no|  
|**vfprintf\_p**|[fprintf\_p](../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)|*資料流*|檢查是否為 null 和格式是否有效。|yes|  
|`vfprintf_s`|[fprintf\_s](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|*資料流*|檢查是否為 null 和格式是否有效。|no|  
|`vfwprintf`|[fwprintf](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|*資料流*|檢查是否為 null 。|no|  
|**vfwprintf\_p**|[fwprintf\_p](../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)|*資料流*|檢查是否為 null 和是否為有效格式。|yes|  
|`vfwprintf_s`|[fwprintf\_s](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|*資料流*|檢查是否為 null 和是否為有效格式。|no|  
|`vprintf`|[printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|`Stdout`|檢查是否為 null 。|no|  
|**vprintf\_p**|[printf\_p](../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)|`Stdout`|檢查是否為 null 和是否為有效格式。|yes|  
|`vprintf_s`|[printf\_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|`Stdout`|檢查是否為 null 和是否為有效格式。|no|  
|`vwprintf`|[wprintf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|`Stdout`|檢查是否為 null 。|no|  
|**vwprintf\_p**|[wprintf\_p](../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)|`Stdout`|檢查是否為 null 和是否為有效格式。|yes|  
|`vwprintf_s`|[wprintf\_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|`Stdout`|檢查是否為 null 和是否為有效格式。|no|  
|**vsprintf**|[sprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)|*buffer* 指向的記憶體|檢查是否為 null 。|no|  
|**vsprintf\_p**|[sprintf\_p](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)|*buffer* 指向的記憶體|檢查是否為 null 和是否為有效格式。|yes|  
|`vsprintf_s`|[sprintf\_s](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|*buffer* 指向的記憶體|檢查是否為 null 和是否為有效格式。|no|  
|`vswprintf`|[swprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)|*buffer* 指向的記憶體|檢查是否為 null 。|no|  
|**vswprintf\_p**|[swprintf\_p](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)|*buffer* 指向的記憶體|檢查是否為 null 和是否為有效格式。|yes|  
|`vswprintf_s`|[swprintf\_s](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|*buffer* 指向的記憶體|檢查是否為 null 和是否為有效格式。|no|  
|`_vscprintf`|[\_vscprintf](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|*buffer* 指向的記憶體|檢查是否為 null 。|no|  
|`_vscwprintf`|[\_vscwprintf](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|*buffer* 指向的記憶體|檢查是否為 null 。|no|  
|`_vsnprintf`|[\_snprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)|*buffer* 指向的記憶體|檢查是否為 null 。|no|  
|`_vsnwprintf`|[\_snwprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)|*buffer* 指向的記憶體|檢查是否為 null 。|no|  
  
 `argptr` 參數的型別為定義於 VARARGS.H 和 STDARG.H 的 `va_list` 。  `argptr` 變數必須以 **va\_start,** 初始化並可以再呼叫 `va_arg` 重新初始化。然後 `argptr` 指向轉換後的參數列的開頭並根據 *format* 參數所指定地傳輸予輸出。  *format* 與 [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) 的 *format* 參數有相同的格式和功能。  這些函式都不會調用 `va_end`。  如需更多完整關於每個 `vprintf` 函式的敍述，請參閱前表中它們相對的函式的敍述說明。  
  
 `_vsnprintf` 與 **vsprintf** 不同的地方在於它不會寫入 *buffer* 超過 *count* 個位元組。  
  
 這些函式名字包含綴字 **w** 的版本是沒有綴字 **w** 者的寬字元版本。在每個這些寬字元版本的函式中 *buffer* 和 *format* 都是寬字元字串。  否則，每個寬字元函式與其 SBCS 相對應函式行為相同。  
  
 這些函式以 **\_s** 和 **\_p** 後綴的版本是更安全的版本。  這些版本的函式會驗證格式字串並在它們的格式不正確時產生例外狀況 \(例如使用了不正確的格式字元\) 。  
  
 這些函式以 **\_p** 後綴的版本提供指定參數在格式字串中替換的順序的功能。  如需詳細資訊，請參閱[printf\_p 位置參數](../c-runtime-library/printf-p-positional-parameters.md)。  
  
 如果在兩相重疊的字串上執行複製， **vsprintf** 、 `vswprintf` 、 `_vsnprintf` 和 `_vsnwprintf` 的行為是未定義的。  
  
> [!IMPORTANT]
>  須確定 *format* 不是一個使用者定義的字串。  如需詳細資訊，請參閱 [Avoiding Buffer Overruns](http://msdn.microsoft.com/library/windows/desktop/ms717795) 。  如果使用這些函式的安全版本 \(以 **\_s** 或 **\_p** 為後綴\)，若使用者提供的格式字串包含無效的格式字元則會觸發無效參數的例外狀況。  
  
## 請參閱  
 [資料流 I\/O](../c-runtime-library/stream-i-o.md)   
 [fprintf、\_fprintf\_l、fwprintf、\_fwprintf\_l](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf、\_printf\_l、wprintf、\_wprintf\_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf、\_sprintf\_l、swprintf、\_swprintf\_l、\_\_swprintf\_l](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [va\_arg、va\_copy、va\_end、va\_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)