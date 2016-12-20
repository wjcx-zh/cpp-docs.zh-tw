---
title: "_snprintf_s、_snprintf_s_l、_snwprintf_s、_snwprintf_s_l | Microsoft Docs"
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
  - "_snprintf_s"
  - "_snprintf_s_l"
  - "_snwprintf_s"
  - "_snwprintf_s_l"
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
  - "_snwprintf_s_l"
  - "_sntprintf_s_l"
  - "snprintf_s_l"
  - "_snprintf_s_l"
  - "_sntprintf_s"
  - "_snprintf_s"
  - "snprintf_s"
  - "_snwprintf_s"
  - "snwprintf_s_l"
  - "snwprintf_s"
  - "sntprintf_s"
  - "sntprintf_s_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_snprintf_s 函式"
  - "_snprintf_s_l 函式"
  - "_sntprintf_s 函式"
  - "_sntprintf_s_l 函式"
  - "_snwprintf_s 函式"
  - "_snwprintf_s_l 函式"
  - "格式化的文字 [C++]"
  - "snprintf_s 函式"
  - "snprintf_s_l 函式"
  - "sntprintf_s 函式"
  - "sntprintf_s_l 函式"
  - "snwprintf_s 函式"
  - "snwprintf_s_l 函式"
ms.assetid: 9336ab86-13e5-4a29-a3cd-074adfee6891
caps.latest.revision: 32
caps.handback.revision: 32
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _snprintf_s、_snprintf_s_l、_snwprintf_s、_snwprintf_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將格式化資料寫入字串。 這些是舊版 [snprintf、\_snprintf、\_snprintf\_l、\_snwprintf、\_snwprintf\_l](../../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md) 中所述的安全性增強 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)。  
  
## 語法  
  
```  
int _snprintf_s(  
   char *buffer,  
   size_t sizeOfBuffer,  
   size_t count,  
   const char *format [,  
   argument] ...   
);  
int _snprintf_s_l(  
   char *buffer,  
   size_t sizeOfBuffer,  
   size_t count,  
   const char *format,  
   locale_t locale [,  
   argument] ...   
);  
int _snwprintf_s(  
   wchar_t *buffer,  
   size_t sizeOfBuffer,  
   size_t count,  
   const wchar_t *format [,  
   argument] ...   
);  
int _snwprintf_s_l(  
   wchar_t *buffer,  
   size_t sizeOfBuffer,  
   size_t count,  
   const wchar_t *format,  
   locale_t locale [,  
   argument] ...   
);  
template <size_t size>  
int _snprintf_s(  
   char (&buffer)[size],  
   size_t count,  
   const char *format [,  
   argument] ...   
); // C++ only  
template <size_t size>  
int _snwprintf_s(  
   wchar_t (&buffer)[size],  
   size_t count,  
   const wchar_t *format [,  
   argument] ...   
); // C++ only  
```  
  
#### 參數  
 `buffer`  
 輸出的儲存位置。  
  
 `sizeOfBuffer`  
 輸出的儲存位置的大小。 調整大小 `bytes` 的 `_snprintf_s` 或大小 `words` 的 `_snwprintf_s`。  
  
 `Count`  
 要儲存的字元數目上限或 [\_TRUNCATE](../../c-runtime-library/truncate.md)。  
  
 `format`  
 格式控制字串。  
  
 `argument`  
 選擇性引數。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 `_snprintf_s` 傳回儲存在中的字元數 `buffer`, ，不計結束的 null 字元。`_snwprintf_s` 會傳回儲存在 `buffer` 中的寬字元數目，不計結束的 null 寬字元。  
  
 如果儲存資料和結束的 null 所需的儲存體超過 `sizeOfBuffer`, 、 無效參數處理常式叫用時，所述 [參數驗證](../../c-runtime-library/parameter-validation.md)。 如果不正確的參數處理常式之後繼續執行，這些函式會將 `buffer` 為空字串，設定 `errno` 至 `ERANGE`, ，並傳回\-1。  
  
 如果 `buffer` 或 `format` 是 `NULL` 指標，或如果 `count` 小於或等於零，會叫用無效參數處理常式。 如果允許繼續執行，這些函式會將 `errno` 設為 `EINVAL`，並傳回 \-1。  
  
 如需有關這些錯誤碼和其他錯誤碼的資訊，請參閱 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 `_snprintf_s` 函式的格式化並儲存 `count` 或較少的字元 `buffer` ，並將結束的 null。 每個引數 （如果有的話） 會轉換和輸出中的對應格式規格根據 `format`。 格式都是一致的 `printf` 系列的函式; 請參閱 [格式規格語法：printf 和 wprintf 函式](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。 如果在重疊的字串之間進行複製，則行為是未定義的。  
  
 如果 `count` 是 [\_TRUNCATE](../../c-runtime-library/truncate.md), ，然後 `_snprintf_s` 盡量將字串寫入以致於無法納入 `buffer` 時留出空間給結束的 null。 如果整個字串 （含結束 null\) 納入 `buffer`, ，然後 `_snprintf_s` 傳回寫入字元數目 （不包括結束的 null）; 否則 `_snprintf_s` 會傳回 – 1，表示該截斷發生。  
  
> [!IMPORTANT]
>  確認 `format` 不是使用者定義的字串。  
  
 `_snwprintf_s` 是 `_snprintf_s` 的寬字元版本，`_snwprintf_s` 的指標引數是寬字元字串。`_snwprintf_s` 中的編碼錯誤偵測可能不同於 `_snprintf_s`。`_snwprintf_s`, 像是 `swprintf_s`, ，為字串，而不是類型的目的地會將輸出寫入 `FILE`。  
  
 這些有 `_l` 尾碼的函式版本是一樣的，不同之處在於會使用傳入的地區設定，而不使用目前的執行緒地區設定。  
  
 C\+\+ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 \(因而不須指定大小引數\)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE 和 \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_sntprintf_s`|`_snprintf_s`|`_snprintf_s`|`_snwprintf_s`|  
|`_sntprintf_s_l`|`_snprintf_s_l`|`_snprintf_s_l`|`_snwprintf_s_l`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_snprintf_s`, `_snprintf_s_l`|\<stdio.h\>|  
|`_snwprintf_s`, `_snwprintf_s_l`|\<stdio.h\> 或 \<wchar.h\>|  
  
 如需相容性詳細資訊，請參閱簡介中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_snprintf_s.cpp  
// compile with: /MTd  
  
// These #defines enable secure template overloads  
// (see last part of Examples() below)  
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES 1   
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT 1  
  
#include <stdio.h>  
#include <stdlib.h>  
#include <string.h>  
#include <crtdbg.h>  // For _CrtSetReportMode  
#include <errno.h>  
  
// This example uses a 10-byte destination buffer.  
  
int snprintf_s_tester( const char * fmt, int x, size_t count )  
{  
   char dest[10];  
  
   printf( "\n" );  
  
   if ( count == _TRUNCATE )  
      printf( "%zd-byte buffer; truncation semantics\n",  
               _countof(dest) );  
   else  
      printf( "count = %zd; %zd-byte buffer\n",  
               count, _countof(dest) );  
  
   int ret = _snprintf_s( dest, _countof(dest), count, fmt, x );  
  
   printf( "    new contents of dest: '%s'\n", dest );  
  
   return ret;  
}  
  
void Examples()  
{  
   // formatted output string is 9 characters long: "<<<123>>>"  
   snprintf_s_tester( "<<<%d>>>", 121, 8 );  
   snprintf_s_tester( "<<<%d>>>", 121, 9 );  
   snprintf_s_tester( "<<<%d>>>", 121, 10 );  
  
   printf( "\nDestination buffer too small:\n" );  
  
   snprintf_s_tester( "<<<%d>>>", 1221, 10 );  
  
   printf( "\nTruncation examples:\n" );  
  
   int ret = snprintf_s_tester( "<<<%d>>>", 1221, _TRUNCATE );  
   printf( "    truncation %s occur\n", ret == -1 ? "did"  
                                                  : "did not" );  
  
   ret = snprintf_s_tester( "<<<%d>>>", 121, _TRUNCATE );  
   printf( "    truncation %s occur\n", ret == -1 ? "did"  
                                                  : "did not" );  
   printf( "\nSecure template overload example:\n" );  
  
   char dest[10];  
   _snprintf( dest, 10, "<<<%d>>>", 12321 );  
   // With secure template overloads enabled (see #defines  
   // at top of file), the preceding line is replaced by  
   //    _snprintf_s( dest, _countof(dest), 10, "<<<%d>>>", 12345 );  
   // Instead of causing a buffer overrun, _snprintf_s invokes  
   // the invalid parameter handler.  
   // If secure template overloads were disabled, _snprintf would  
   // write 10 characters and overrun the dest buffer.  
   printf( "    new contents of dest: '%s'\n", dest );  
}  
  
void myInvalidParameterHandler(  
   const wchar_t* expression,  
   const wchar_t* function,   
   const wchar_t* file,   
   unsigned int line,   
   uintptr_t pReserved)  
{  
   wprintf(L"Invalid parameter handler invoked: %s\n", expression);  
}  
  
int main( void )  
{  
   _invalid_parameter_handler oldHandler, newHandler;  
  
   newHandler = myInvalidParameterHandler;  
   oldHandler = _set_invalid_parameter_handler(newHandler);  
   // Disable the message box for assertions.  
   _CrtSetReportMode(_CRT_ASSERT, 0);  
  
   Examples();  
}  
```  
  
```Output  
  
計數 = 8。10 位元組緩衝區的新內容的目的地: '<<< 121 >>' 計數 = 9。10 位元組緩衝區的新內容的目的地: '<<< 121 >>> ' 計數 = 10。10 位元組緩衝區的新內容的目的地: '<<< 121 >>> ' 目的緩衝區太小︰ 計數 = 10。10 位元組緩衝區無效參數處理常式叫用: (「 緩衝區太小 」，0) 的目的地的新內容: ' 截斷範例︰ 10 位元組緩衝區。截斷語意 （semantics） 的新內容目的地: '<<< 1221 >>' 並未發生截斷 10 位元組緩衝區。截斷語意 （semantics） 的新內容目的地: '<<< 121 >>> ' 截斷並未發生安全範本多載範例︰ 叫用無效參數處理常式: (「 緩衝區太小 」，0) 的目的地的新內容: '  
```  
  
## .NET Framework 對等用法  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [sprintf、\_sprintf\_l、swprintf、\_swprintf\_l、\_\_swprintf\_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [fprintf、\_fprintf\_l、fwprintf、\_fwprintf\_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf、\_printf\_l、wprintf、\_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [scanf、\_scanf\_l、wscanf、\_wscanf\_l](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [sscanf、\_sscanf\_l、swscanf、\_swscanf\_l](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)   
 [vprintf 函式](../../c-runtime-library/vprintf-functions.md)