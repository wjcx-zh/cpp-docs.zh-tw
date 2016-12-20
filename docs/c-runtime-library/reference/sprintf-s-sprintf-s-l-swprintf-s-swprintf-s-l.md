---
title: "sprintf_s、_sprintf_s_l、swprintf_s、_swprintf_s_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_swprintf_s_l"
  - "_sprintf_s_l"
  - "swprintf_s"
  - "sprintf_s"
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
  - "swprintf_s"
  - "sprintf_s"
  - "stdio/sprintf_s"
  - "stdio/swprintf_s"
  - "stdio/_sprintf_s_l"
  - "stdio/_swprintf_s_l"
  - "_sprintf_s_l"
  - "_swprintf_s_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "stprintf_s 函式"
  - "stprintf_s_l 函式"
  - "swprintf_s_l 函式"
  - "sprintf_s 函式"
  - "swprintf_s 函式"
  - "_swprintf_s_l 函式"
  - "sprintf_s_l 函式"
  - "_stprintf_s_l 函式"
  - "_stprintf_s 函式"
  - "_sprintf_s_l 函式"
  - "格式化的文字 [C++]"
ms.assetid: 424f0a29-22ef-40e8-b565-969f5f57782f
caps.latest.revision: 26
caps.handback.revision: 26
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# sprintf_s、_sprintf_s_l、swprintf_s、_swprintf_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將格式化資料寫入字串。 這些是 [sprintf、\_sprintf\_l、swprintf、\_swprintf\_l、\_\_swprintf\_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md) 的安全性增強版本，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md) 中所述。  
  
## 語法  
  
```  
int sprintf_s(  
   char *buffer,  
   size_t sizeOfBuffer,  
   const char *format,  
   ...   
);  
int _sprintf_s_l(  
   char *buffer,  
   size_t sizeOfBuffer,  
   const char *format,  
   locale_t locale,  
   ...   
);  
int swprintf_s(  
   wchar_t *buffer,  
   size_t sizeOfBuffer,  
   const wchar_t *format,  
   ...  
);  
int _swprintf_s_l(  
   wchar_t *buffer,  
   size_t sizeOfBuffer,  
   const wchar_t *format,  
   locale_t locale,  
   ...  
);  
template <size_t size>  
int sprintf_s(  
   char (&buffer)[size],  
   const char *format,  
   ...   
); // C++ only  
template <size_t size>  
int swprintf_s(  
   wchar_t (&buffer)[size],  
   const wchar_t *format,  
   ...  
); // C++ only  
```  
  
#### 參數  
 `buffer`  
 輸出的儲存位置  
  
 `sizeOfBuffer`  
 要儲存的最大字元數。  
  
 `format`  
 格式控制字串  
  
 `...`  
 要進行格式化的選擇性引數  
  
 `locale`  
 要使用的地區設定。  
  
 如需詳細資訊，請參閱[格式規格](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。  
  
## 傳回值  
 寫入的字元數目，如果發生錯誤則為 \-1。 如果 `buffer` 或 `format` 為 null 指標、則 `sprintf_s` 和 `swprintf_s` 會傳回 \-1，並將 `errno` 設定為 `EINVAL`。  
  
 `sprintf_s` 會傳回儲存在 `buffer` 中的位元組數目，不計結束的 null 字元。`swprintf_s` 會傳回儲存在 `buffer` 中的寬字元數目，不計結束的 null 寬字元。  
  
## 備註  
 `sprintf_s` 函式會在 `buffer` 中格式化並儲存一連串字元和值。 每個 `argument` \(如果有的話\) 是根據 `format` 中的對應格式規格進行轉換和輸出。 此格式包含一般字元，與 [printf](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) 的 `format` 引數具有相同的形式和功能。 null 字元會附加至最後一個寫入的字元之後。 如果在重疊的字串之間進行複製，則行為是未定義的。  
  
 `sprintf_s` 和 `sprintf` 之間有一個主要差異，即在於 `sprintf_s` 會檢查格式字串中的格式化字元是否有效，而 `sprintf` 只檢查格式字串或緩衝區是否為 `NULL` 指標。 若其中一個檢查失敗，就會叫用無效的參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 所述。 如果允許繼續執行，則函式會傳回 \-1 並將 `errno` 設定為 `EINVAL`。  
  
 `sprintf_s` 和 `sprintf` 之間的另一個主要差異在於 `sprintf_s` 接受指定輸出緩衝區大小 \(以字元為單位\) 的長度參數。 若緩衝區對格式化文字而言太小 \(包括結尾的 null\)，就會藉由 null 字元放在 `buffer``[0]`，將緩衝區設為空字串，並叫用無效的參數處理常式。 與 `_snprintf` 不同的是，`sprintf_s` 保證緩衝區會以 null 結尾 \(除非緩衝區大小為零\)。  
  
 `swprintf_s` 是 `sprintf_s` 的寬字元版本，`swprintf_s` 的指標引數是寬字元字串。`swprintf_s` 的編碼錯誤偵測可能不同於 `sprintf_s`。 這些有 `_l` 尾碼的函式版本是一樣的，不同之處在於會使用傳入的地區設定，而不使用目前的執行緒地區設定。  
  
 在 C\+\+ 中，範本多載簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 \(因而不需指定大小引數\)，也可將不安全的較舊函式自動取代成較新且安全的對應函式。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
 對於緩衝區太小時的處理方式，有些 `sprintf_s` 版本會提供更多的控制。 如需詳細資訊，請參閱[\_snprintf\_s、\_snprintf\_s\_l、\_snwprintf\_s、\_snwprintf\_s\_l](../../c-runtime-library/reference/snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md)。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE 和 \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_stprintf_s`|`sprintf_s`|`sprintf_s`|`swprintf_s`|  
|`_stprintf_s_l`|`_sprintf_s_l`|`_sprintf_s_l`|`_swprintf_s_l`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`sprintf_s`、 `_sprintf_s_l`|C：\<stdio.h\><br /><br /> C\+\+：\<cstdio\> 或 \<stdio.h\>|  
|`swprintf_s`、 `_swprintf_s_l`|C：\<stdio.h\> 或 \<wchar.h\><br /><br /> C\+\+：\<cstdio\>、\<cwchar\>、\<stdio.h\> 或 \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_sprintf_s.c  
// This program uses sprintf_s to format various  
// data and place them in the string named buffer.  
//  
  
#include <stdio.h>  
  
int main( void )  
{  
   char  buffer[200], s[] = "computer", c = 'l';  
   int   i = 35, j;  
   float fp = 1.7320534f;  
  
   // Format and print various data:   
   j  = sprintf_s( buffer, 200,     "   String:    %s\n", s );  
   j += sprintf_s( buffer + j, 200 - j, "   Character: %c\n", c );  
   j += sprintf_s( buffer + j, 200 - j, "   Integer:   %d\n", i );  
   j += sprintf_s( buffer + j, 200 - j, "   Real:      %f\n", fp );  
  
   printf_s( "Output:\n%s\ncharacter count = %d\n", buffer, j );  
}  
```  
  
```Output  
輸出：字串：computer 字元：l 整數：35 實數：1.732053 字元計數 = 79  
```  
  
## 範例  
  
```  
// crt_swprintf_s.c  
// wide character example  
// also demonstrates swprintf_s returning error code  
#include <stdio.h>  
  
int main( void )  
{  
   wchar_t buf[100];  
   int len = swprintf_s( buf, 100, L"%s", L"Hello world" );  
   printf( "wrote %d characters\n", len );  
   len = swprintf_s( buf, 100, L"%s", L"Hello\xffff world" );  
   // swprintf_s fails because string contains WEOF (\xffff)  
   printf( "wrote %d characters\n", len );  
}  
```  
  
```Output  
已寫入 11 個字元已寫入 -1 個字元  
```  
  
## .NET Framework 對等用法  
 [System::String::Format](https://msdn.microsoft.com/en-us/library/system.string.format.aspx)  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fprintf、\_fprintf\_l、fwprintf、\_fwprintf\_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf、\_printf\_l、wprintf、\_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [scanf、\_scanf\_l、wscanf、\_wscanf\_l](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [sscanf、\_sscanf\_l、swscanf、\_swscanf\_l](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)   
 [vprintf 函式](../../c-runtime-library/vprintf-functions.md)