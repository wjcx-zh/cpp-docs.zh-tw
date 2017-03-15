---
title: "strerror_s、_strerror_s、_wcserror_s、__wcserror_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "__wcserror_s"
  - "_strerror_s"
  - "_wcserror_s"
  - "strerror_s"
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
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "wcserror_s"
  - "__wcserror_s"
  - "_tcserror_s"
  - "_wcserror_s"
  - "tcserror_s"
  - "strerror_s"
  - "_strerror_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__wcserror_s 函式"
  - "_strerror_s 函式"
  - "_tcserror_s 函式"
  - "_wcserror_s 函式"
  - "錯誤訊息, 取得"
  - "錯誤訊息, 列印"
  - "列印錯誤訊息"
  - "strerror_s 函式"
  - "tcserror_s 函式"
  - "wcserror_s 函式"
ms.assetid: 9e5b15a0-efe1-4586-b7e3-e1d7c31a03d6
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# strerror_s、_strerror_s、_wcserror_s、__wcserror_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

取得系統錯誤訊息 \(`strerror_s`、 `_wcserror_s`\) 或列印一使用者提供的錯誤訊息 \(`_strerror_s`、 `__wcserror_s`\)。  這些是 [strerror、\_strerror、\_wcserror、\_\_wcserror](../../c-runtime-library/reference/strerror-strerror-wcserror-wcserror.md) 的安全性增強版本，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md) 中所述。  
  
## 語法  
  
```  
errno_t strerror_s(  
   char *buffer,  
   size_t numberOfElements,  
   int errnum   
);  
errno_t _strerror_s(  
   char *buffer,  
   size_t numberOfElements,  
   const char *strErrMsg   
);  
errno_t _wcserror_s(  
   wchar_t *buffer,  
   size_t numberOfElements,  
   int errnum   
);  
errno_t __wcserror_s(  
   wchar_t *buffer,  
   size_t numberOfElements,  
   const wchar_t *strErrMsg   
);  
template <size_t size>  
errno_t strerror_s(  
   char (&buffer)[size],  
   int errnum   
); // C++ only  
template <size_t size>  
errno_t _strerror_s(  
   char (&buffer)[size],  
   const char *strErrMsg   
); // C++ only  
template <size_t size>  
errno_t _wcserror_s(  
   wchar_t (&buffer)[size],  
   int errnum   
); // C++ only  
template <size_t size>  
errno_t __wcserror_s(  
   wchar_t (&buffer)[size],  
   const wchar_t *strErrMsg   
); // C++ only  
```  
  
#### 參數  
 `buffer`  
 保留錯誤字串的緩衝區。  
  
 `numberOfElements`  
 緩衝區大小。  
  
 `errnum`  
 錯誤代碼。  
  
 `strErrMsg`  
 使用者提供的訊息。  
  
## 傳回值  
 若成功則為零，失敗則為錯誤碼。  
  
### 錯誤狀況  
  
|`buffer`|`numberOfElements`|`strErrMsg`|`buffer` 的內容|  
|--------------|------------------------|-----------------|------------------|  
|`NULL`|any|any|N\/A|  
|any|0|any|未修改|  
  
## 備註  
 `strerror_s` 函式會將 `errnum` 對應到錯誤訊息字串，傳回 `buffer` 中的字串。  `_strerror_s` 未採用錯誤代碼；它會使用 `errno` 的目前值決定適當的訊息。  `strerror_s` 和 `_strerror_s` 實際上不會輸出訊息：因此，您需要呼叫一個輸出函式 \(例如 [fprintf](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)\)：  
  
```  
if (( _access( "datafile",2 )) == -1 )  
{  
   _strerror_s(buffer, 80);  
   fprintf( stderr, buffer );  
}  
```  
  
 如果 `strErrMsg` 是 `NULL`， `_strerror_s` 會傳回 `buffer` 中的字串，此字串包含系統錯誤訊息 \(造成錯誤的最後函式庫呼叫\)。  錯誤訊息字串是由新行字元 \(「\\ n 」結束\)。  如果 `strErrMsg` 不等於 `NULL`，則 `_strerror_s` 會傳回在 `buffer` 中包含 \(依順序\) 您的字串訊息 、逗號、空格、系統錯誤訊息 \(造成錯誤的最後程式庫呼叫\) 和新行字元的字串。  您的字串訊息最多可以是 94 個字元長度。  
  
 如果其長度超過 `numberOfElements` \-1，這些函式會截斷錯誤訊息。  在 `buffer` 中產生的字串一定是 null 結尾。  
  
 `_strerror_s` 的實際錯誤代碼儲存在變數 [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 中。  系統錯誤訊息透過變數 [\_sys\_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 存取，此變數為依錯誤代碼排序的訊息陣列。  `_strerror_s` 使用 `errno` 值做為對變數 `_sys_errlist` 的索引，存取適當的錯誤訊息。  [\_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 變數的值定義為項目 `_sys_errlist` 陣列中的最大數目。  若要產生正確的結果，請在程式庫常式傳回錯誤之後立刻呼叫 `_strerror_s`。  否則，`strerror_s` 或 `_strerror_s` 的後續呼叫可以覆寫 `errno` 值。  
  
 `_wcserror_s`、 和  `__wcserror_s` 分別為 `strerror_s` 和 `_strerror_s` 的寬字元版本。  
  
 這些函式會驗證它們的參數。  如果緩衝區是 `NULL` ，或如果大小參數是 0，無效的參數處理常式會被叫用，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，函式會傳回 `EINVAL` 並將 `errno` 設定為 `EINVAL`。  
  
 `_strerror_s, _wcserror_s,` 和 `__wcserror_s`  不為 ANSI 定義的部分，而由 Microsoft 擴充它。  不要使用其可攜性所要的位置；若為 ANSI 相容性，請改用 `strerror_s` 。  
  
 在 C\+\+ 中，這些函式的使用被簡化為使用樣板多載；使用多載可以自動推斷緩衝區的大小而不必在參數中指明大小。  如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
 這些函式的偵錯版本會先用 0xFD 填入緩衝區。  若要停用此行為，請使用 [\_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md)。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcserror_s`|`strerror_s`|`strerror_s`|`_wcserror_s`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`strerror_s`, `_strerror_s`|\<string.h\>|  
|`_wcserror_s`, `__wcserror_s`|\<string.h\> 或 \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
 請參閱 [perror](../../c-runtime-library/reference/perror-wperror.md) 的範例。  
  
## .NET Framework 對等用法  
 [System::Exception::Message](https://msdn.microsoft.com/en-us/library/system.exception.message.aspx)  
  
## 請參閱  
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [clearerr](../../c-runtime-library/reference/clearerr.md)   
 [ferror](../../c-runtime-library/reference/ferror.md)   
 [perror、\_wperror](../../c-runtime-library/reference/perror-wperror.md)