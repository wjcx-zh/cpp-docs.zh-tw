---
title: "vsnprintf_s、_vsnprintf_s、_vsnprintf_s_l、_vsnwprintf_s、_vsnwprintf_s_l | Microsoft Docs"
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
  - "_vsnwprintf_s"
  - "_vsnwprintf_s_l"
  - "_vsnprintf_s"
  - "vsnprintf_s"
  - "_vsnprintf_s_l"
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
  - "_vsnprintf_s"
  - "_vsntprintf_s"
  - "_vsnwprintf_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_vsnprintf_s 函式"
  - "_vsnprintf_s_l 函式"
  - "_vsntprintf_s 函式"
  - "_vsntprintf_s_l 函式"
  - "_vsnwprintf_s 函式"
  - "_vsnwprintf_s_l 函式"
  - "格式化的文字 [C++]"
  - "vsnprintf_s 函式"
  - "vsnprintf_s_l 函式"
  - "vsntprintf_s 函式"
  - "vsntprintf_s_l 函式"
  - "vsnwprintf_s 函式"
  - "vsnwprintf_s_l 函式"
ms.assetid: 147ccfce-58c7-4681-a726-ef54ac1c604e
caps.latest.revision: 30
caps.handback.revision: 28
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# vsnprintf_s、_vsnprintf_s、_vsnprintf_s_l、_vsnwprintf_s、_vsnwprintf_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用指向一個引數清單的指標輸出格式化的字串  這些是 [vsnprintf、\_vsnprintf、\_vsnprintf\_l、\_vsnwprintf、\_vsnwprintf\_l](../../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) 的安全性增強版本，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md) 中所述。  
  
## 語法  
  
```  
int vsnprintf_s(  
   char *buffer,  
   size_t sizeOfBuffer,  
   size_t count,  
   const char *format,  
   va_list argptr   
);  
int _vsnprintf_s(  
   char *buffer,  
   size_t sizeOfBuffer,  
   size_t count,  
   const char *format,  
   va_list argptr   
);  
int _vsnprintf_s_l(  
   char *buffer,  
   size_t sizeOfBuffer,  
   size_t count,  
   const char *format,  
   locale_t locale,  
   va_list argptr   
);  
int _vsnwprintf_s(  
   wchar_t *buffer,  
   size_t sizeOfBuffer,  
   size_t count,  
   const wchar_t *format,  
   va_list argptr   
);  
int _vsnwprintf_s_l(  
   wchar_t *buffer,  
   size_t sizeOfBuffer,  
   size_t count,  
   const wchar_t *format,  
   locale_t locale,  
   va_list argptr   
);  
template <size_t size>  
int _vsnprintf_s(  
   char (&buffer)[size],  
   size_t count,  
   const char *format,  
   va_list argptr   
); // C++ only  
template <size_t size>  
int _vsnwprintf_s(  
   wchar_t (&buffer)[size],  
   size_t count,  
   const wchar_t *format,  
   va_list argptr   
); // C++ only  
```  
  
#### 參數  
 `buffer`  
 輸出的儲存位置。  
  
 `sizeOfBuffer`  
 用以輸出的`buffer` 大小，做為字元計數。  
  
 `count`  
 寫入的字元數上限 \(不含結尾的 NULL\)，或 [\_TRUNCATE](../../c-runtime-library/truncate.md)。  
  
 `format`  
 格式規範。  
  
 `argptr`  
 參數清單的指標。  
  
 `locale`  
 使用的地區設定。  
  
 如需詳細資訊，請參閱[格式規格](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。  
  
## 傳回值  
 `vsnprintf_s`,`_vsnprintf_s` 和 `_vsnwprintf_s`  回傳寫入的字元數，不包含結尾的空字元，或者在輸出發生錯誤時回傳一個負值。  `vsnprintf_s` 與 `_vsnprintf_s`相同。  `vsnprintf_s` 是為了相容 ANSI 標準而加入。  保留 `_vnsprintf` 以達到回溯相容性。  
  
 如果要求的儲存體儲存資料加上一個結尾的 NULL 超出 `sizeOfBuffer`，將叫用無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述，除非， `count` 是 [\_TRUNCATE](../../c-runtime-library/truncate.md)，在這種情況下，寫入與 `buffer` 相同大小的字串並回傳 \-1。  如果運行無效參數處理常式之後繼續執行，這些函式將 `buffer` 設為空字串，將 `errno` 設為 `ERANGE`並傳回 \-1。  
  
 如果 `buffer` 或 `format` 是 `NULL` 指標，或者，如果 `count` 小於或等於零，無效參數處理常式將被叫用。  如果允許繼續執行，這些函式會將 `errno` 設定為 `EINVAL` 並傳回 \-1。  
  
### 錯誤狀況  
  
|`Condition`|Return|`errno`|  
|-----------------|------------|-------------|  
|`buffer` 為  `NULL`|\-1|`EINVAL`|  
|`format` 為  `NULL`|\-1|`EINVAL`|  
|`count` \<\= 0|\-1|`EINVAL`|  
|`sizeOfBuffer` 太小\(與 `count` \! \= `_TRUNCATE`\)|\-1 \(與 `buffer` 是設定為空字串\)。|`ERANGE`|  
  
## 備註  
 這些函式取得指標指向引數清單，然後格式化並寫入 `count` 個字元至被 `buffer` 指向的記憶體並附加一個結尾的 NULL。  
  
 如果 `count` 是 [\_TRUNCATE](../../c-runtime-library/truncate.md)，則這些函式寫入與 `buffer` 相同大小的字串，並留空間給結尾的 NULL。  如果整個字串 \(加上結尾 NULL\) 符合 `buffer` 的大小，這些函式會傳回寫入的字元數 \(不含結尾的 NULL\);否則，這些函式傳回 \-1 以表示字串被截斷。  
  
 尾碼為 `_l` 的這些函式版本是一樣的，只不過它們使用傳入的地區設定，而不是目前執行緒的地區設定。  
  
> [!IMPORTANT]
>  確認 `format` 不是使用者定義的字串。  如需詳細資訊，請參閱 [Avoiding Buffer Overruns](http://msdn.microsoft.com/library/windows/desktop/ms717795) 。  
  
> [!NOTE]
>  若要確保有空間給結尾 NULL，請確定 `count` 嚴格小於緩衝區的長度，或使用 `_TRUNCATE`。  
  
 C\+\+ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 \(因而不須指定大小引數\)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。  如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_vsntprintf_s`|`_vsnprintf_s`|`_vsnprintf_s`|`_vsnwprintf_s`|  
|`_vsntprintf_s_l`|`_vsnprintf_s_l`|`_vsnprintf_s_l`|`_vsnwprintf_s_l`|  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 需求  
  
|常式|必要的標頭|選擇性的標頭檔|  
|--------|-----------|-------------|  
|`vsnprintf_s`|\<stdio.h\> 和 \<stdarg.h\>|\<varargs.h\>\*|  
|`_vsnprintf_s`, `_vsnprintf_s_l`|\<stdio.h\> 和 \<stdarg.h\>|\<varargs.h\>\*|  
|`_vsnwprintf_s`, `_vsnwprintf_s_l`|\<stdio.h\> 或 \<wchar.h\>, 及 \<stdarg.h\>|\<varargs.h\>\*|  
  
 \* 要求 UNIX V 相容性。  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_vsnprintf_s.cpp  
#include <stdio.h>  
#include <wtypes.h>  
  
void FormatOutput(LPCSTR formatstring, ...)   
{  
   int nSize = 0;  
   char buff[10];  
   memset(buff, 0, sizeof(buff));  
   va_list args;  
   va_start(args, formatstring);  
   nSize = vsnprintf_s( buff, _countof(buff), _TRUNCATE, formatstring, args);  
   printf("nSize: %d, buff: %s\n", nSize, buff);  
}  
  
int main() {  
   FormatOutput("%s %s", "Hi", "there");  
   FormatOutput("%s %s", "Hi", "there!");  
   FormatOutput("%s %s", "Hi", "there!!");  
}  
```  
  
  **nSize: 8，buff: Hi there**  
**nSize: 9，buff: Hi there\!**  
**nSize: \-1，buff: Hi there\!**   
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [vprintf 函式](../../c-runtime-library/vprintf-functions.md)   
 [fprintf、\_fprintf\_l、fwprintf、\_fwprintf\_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf、\_printf\_l、wprintf、\_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf、\_sprintf\_l、swprintf、\_swprintf\_l、\_\_swprintf\_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [va\_arg、va\_copy、va\_end、va\_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)