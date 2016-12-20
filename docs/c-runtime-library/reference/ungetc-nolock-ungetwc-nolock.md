---
title: "_ungetc_nolock、_ungetwc_nolock | Microsoft Docs"
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
  - "_ungetwc_nolock"
  - "_ungetc_nolock"
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
  - "api-ms-win-crt-stdio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_ungettc_nolock"
  - "ungetwc_nolock"
  - "ungetc_nolock"
  - "_ungetc_nolock"
  - "_ungetwc_nolock"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ungetc_nolock 函式"
  - "_ungettc_nolock 函式"
  - "_ungetwc_nolock 函式"
  - "字元, 推送回到資料流"
  - "ungetc_nolock 函式"
  - "ungettc_nolock 函式"
  - "ungetwc_nolock 函式"
ms.assetid: aa02d5c2-1be1-46d2-a8c4-b61269e9d465
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ungetc_nolock、_ungetwc_nolock
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

推一個字元到資料流上。  
  
## 語法  
  
```  
int _ungetc_nolock(  
   int c,  
   FILE *stream   
);  
wint_t _ungetwc_nolock(  
   wint_t c,  
   FILE *stream   
);  
```  
  
#### 參數  
 `c`  
 待推回的字元。  
  
 `stream`  
 指向 `FILE` 結構的指標。  
  
## 傳回值  
 如果成功的話，這些函式都會傳回字元引數的 `c`*。*如果 `c` 無法推回，或是未讀取字元，輸入資料流不會變更和 `_ungetc_nolock` 會傳回 `EOF`; `_ungetwc_nolock` 會傳回 `WEOF`。  如果 `stream` 是 `NULL`，傳回 `EOF` 或 `WEOF` ，而且 `errno` 設定為 `EINVAL`。  
  
 如需有關這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 這些函式是 `ungetc` 和 `ungetwc`的非鎖定版本。  有 `_nolock` 結尾的版本是相同的，除非它們受到其他執行緒干擾。  因為它們不會造成鎖定其他執行緒的額外負荷，所以可能會比較快。  這些函式只能用在安全執行緒內容 \(例如單一執行緒應用程式\) 或呼叫範圍已經處理執行緒隔離的地方。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|\_UNICODE & \_MBCS 未定義|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_ungettc_nolock`|`_ungetc_nolock`|`_ungetc_nolock`|`_ungetwc_nolock`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_ungetc_nolock`|\<stdio.h\>|  
|`_ungetwc_nolock`|\<stdio.h\> 或 \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [getc、getwc](../../c-runtime-library/reference/getc-getwc.md)   
 [putc、putwc](../../c-runtime-library/reference/putc-putwc.md)