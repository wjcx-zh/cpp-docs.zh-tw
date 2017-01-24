---
title: "vsnprintf、_vsnprintf、_vsnprintf_l、_vsnwprintf、_vsnwprintf_l | Microsoft Docs"
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
  - "_vsnprintf"
  - "_vsnprintf_l"
  - "_vsnwprintf"
  - "_vsnwprintf_l"
  - "_vsnprintf"
  - "_vsnprintf;"
  - "vsnprintf; _vsnprintf"
  - "_vsnwprintf;"
  - "_vsnprintf_l;"
  - "_vsnwprintf_l;"
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
  - "_vsnprintf"
  - "_vsnwprintf"
  - "_vsntprintf"
  - "vsnprintf"
  - "stdio/vsnprintf"
  - "stdio/_vsnprintf"
  - "stdio/_vsnprintf_l"
  - "stdio/_vsnwprintf"
  - "stdio/_vsnwprintf_l"
  - "_vsnprintf_l"
  - "_vsnwprintf_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "vsntprintf 函式"
  - "_vsnwprintf_l 函式"
  - "vsnwprintf_l 函式"
  - "vsntprintf_l 函式"
  - "_vsntprintf 函式"
  - "_vsnprintf_l 函式"
  - "vsnprintf 函式"
  - "_vsntprintf_l 函式"
  - "vsnprintf_l 函式"
  - "_vsnwprintf 函式"
  - "_vsnprintf 函式"
  - "格式化的文字 [C++]"
  - "vsnwprintf 函式"
ms.assetid: a97f92df-c2f8-4ea0-9269-76920d2d566a
caps.latest.revision: 35
caps.handback.revision: 35
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# vsnprintf、_vsnprintf、_vsnprintf_l、_vsnwprintf、_vsnwprintf_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用引數清單的指標，寫入格式化輸出。 這些函式已有更安全的版本可用，請參閱 [vsnprintf\_s、\_vsnprintf\_s、\_vsnprintf\_s\_l、\_vsnwprintf\_s、\_vsnwprintf\_s\_l](../../c-runtime-library/reference/vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l.md)。  
  
## 語法  
  
```  
int vsnprintf(  
   char *buffer,  
   size_t count,  
   const char *format,  
   va_list argptr   
);  
int _vsnprintf(  
   char *buffer,  
   size_t count,  
   const char *format,  
   va_list argptr   
);  
int _vsnprintf_l(  
   char *buffer,  
   size_t count,  
   const char *format,  
   locale_t locale,  
   va_list argptr   
);  
int _vsnwprintf(  
   wchar_t *buffer,  
   size_t count,  
   const wchar_t *format,  
   va_list argptr   
);  
int _vsnwprintf_l(  
   wchar_t *buffer,  
   size_t count,  
   const wchar_t *format,  
   locale_t locale,  
   va_list argptr   
);  
template <size_t size>  
int vsnprintf(  
   char (&buffer)[size],  
   size_t count,  
   const char *format,  
   va_list argptr   
); // C++ only  
template <size_t size>  
int _vsnprintf(  
   char (&buffer)[size],  
   size_t count,  
   const char *format,  
   va_list argptr   
); // C++ only  
template <size_t size>  
int _vsnprintf_l(  
   char (&buffer)[size],  
   size_t count,  
   const char *format,  
   locale_t locale,  
   va_list argptr   
); // C++ only  
template <size_t size>  
int _vsnwprintf(  
   wchar_t (&buffer)[size],  
   size_t count,  
   const wchar_t *format,  
   va_list argptr   
); // C++ only  
template <size_t size>  
int _vsnwprintf_l(  
   wchar_t (&buffer)[size],  
   size_t count,  
   const wchar_t *format,  
   locale_t locale,  
   va_list argptr   
); // C++ only  
```  
  
#### 參數  
 `buffer`  
 輸出的儲存位置。  
  
 `count`  
 要寫入的最大字元數。  
  
 `format`  
 格式規格。  
  
 `argptr`  
 引數清單的指標。  
  
 `locale`  
 要使用的地區設定。  
  
 如需詳細資訊，請參閱[格式規格](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。  
  
## 傳回值  
 `vsnprintf` 函式會傳回寫入的字元數目，不計結束的 null 字元。 如果所指定的緩衝區大小 `count` 夠大，無法包含所指定的輸出 `format` 和 `argptr`, ，傳回值 `vsnprintf` 是的則會寫入，如果不計算的 null 字元的字元數 `count` 已夠大。 如果傳回的值大於 `count` \-1，已截斷輸出。 傳回值 \-1 表示發生編碼錯誤。  
  
 同時 `_vsnprintf` 和 `_vsnwprintf` 函式會傳回要寫入的字元數字是否小於或等於所寫入的字元數目 `count`; 如果要寫入的字元數為大於 `count`, ，這些函式傳回\-1，表示輸出已被截斷。  
  
 所有這些函式所傳回的值不包含結束的 null，不論其中一個撰寫。 當 `count` 為零，則傳回值的函式會寫入不的字元數包括結束的 null。 您可以使用此結果來配置足夠的緩衝區空間的字串和結束的 null，並接著呼叫一次，以填滿緩衝區函式。  
  
 如果 `format` 是 `NULL`, ，或者如果 `buffer` 是 NULL 和 `count` 不等於零，這些函式叫用無效參數處理常式中所述 [參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，這些函式會傳回 \-1，並將 `errno` 設為 `EINVAL`。  
  
## 備註  
 其中每個函式都會接受引數清單的指標，然後格式化資料，並將最多 `count` 字元寫入 `buffer` 所指向的記憶體。`vsnprintf` 函式一律會寫入 null 結束字元，即使會截斷輸出亦同。 在使用 `_vsnprintf` 和 `_vsnwprintf` 的情況下，僅有當結尾有足夠的空間 \(亦即，要寫入的字元數目小於 `count`\) 時緩衝區才會以 null 終止。  
  
> [!IMPORTANT]
>  若要防止特定種類的安全性風險，請確認 `format` 不是使用者定義的字串。 如需詳細資訊，請參閱 [Avoiding Buffer Overruns \(避免緩衝區滿溢\)](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
> [!NOTE]
>  若要確保在呼叫 `_vsnprintf`，`_vsnprintf_l`，`_vsnwprintf` 與 `_vsnwprintf_l` 時，結尾的 null 有足夠空間，請確認 `count` 絕對小於緩衝區長度，並在呼叫函式前將緩衝區初始化為 null。  
>   
>  因為 `vsnprintf` 一律會寫入結束的 null `count` 參數可以是等於緩衝區的大小。  
  
 自 Visual Studio 2015 及 Windows 10 的 UCRT 起，`vsnprintf` 即不再等同於 `_vsnprintf`。`vsnprintf` 函式符合 C99 標準; `_vnsprintf` 保留舊版的 Visual Studio 程式碼的回溯相容性。  
  
 這些有 `_l` 尾碼的函式版本是一樣的，不同之處在於會使用傳入的地區設定，而不使用目前的執行緒地區設定。  
  
 在 C\+\+ 中，這些函式具有樣板多載，可以叫用這些函式的更新且安全的對應版本。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE 和 \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_vsntprintf`|`_vsnprintf`|`_vsnprintf`|`_vsnwprintf`|  
|`_vsntprintf_l`|`_vsnprintf_l`|`_vsnprintf_l`|`_vsnwprintf_l`|  
  
## 需求  
  
|常式|必要的標頭 \(C\)|必要的標頭 \(C\+\+\)|  
|--------|-----------------|---------------------|  
|`vsnprintf`, `_vsnprintf`, `_vsnprintf_l`|\<stdio.h\>|\<stdio.h\> 或 \<cstdio\>|  
|`_vsnwprintf`, `_vsnwprintf_l`|\<stdio.h\> 或 \<wchar.h\>|\<stdio.h\>、\<wchar.h\>、\<cstdio\> 或 \<cwchar\>|  
  
 `_vsnprintf`、`_vsnprintf_l`、`_vsnwprintf` 與 `_vsnwprintf_l` 函式為 Microsoft 特有。 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```c  
// crt_vsnwprintf.c  
// compile by using: cl /W3 crt_vsnwprintf.c  
  
// To turn off error C4996, define this symbol:  
#define _CRT_SECURE_NO_WARNINGS  
  
#include <stdio.h>  
#include <wtypes.h>  
  
#define BUFFCOUNT (10)  
  
void FormatOutput(LPCWSTR formatstring, ...)  
{  
    int nSize = 0;  
    wchar_t buff[BUFFCOUNT];  
    memset(buff, 0, sizeof(buff));  
    va_list args;  
    va_start(args, formatstring);  
    // Note: _vsnwprintf is deprecated; consider vsnwprintf_s instead  
    nSize = _vsnwprintf(buff, BUFFCOUNT - 1, formatstring, args); // C4996  
    wprintf(L"nSize: %d, buff: %ls\n", nSize, buff);  
}  
  
int main() {  
    FormatOutput(L"%ls %ls", L"Hi", L"there");  
    FormatOutput(L"%ls %ls", L"Hi", L"there!");  
    FormatOutput(L"%ls %ls", L"Hi", L"there!!");  
}  
```  
  
```Output  
nSize: 8 受惠於所加持︰ 大家有 nSize: 9 受惠於所加持︰ 大家那里 ！nSize:-1，受惠於所加持︰ 大家那里 ！  
```  
  
 如果您使用 vsnprintf，以及窄字串參數，就會變更行為。`count` 參數可以是整個緩衝區的大小，而傳回的值會將已寫入如果的字元數 `count` 夠大，足以︰  
  
## 範例  
  
```c  
// crt_vsnprintf.c  
// compile by using: cl /W4 crt_vsnprintf.c  
#include <stdio.h>  
#include <stdarg.h> // for va_list, va_start  
#include <string.h> // for memset  
  
#define BUFFCOUNT (10)  
  
void FormatOutput(char* formatstring, ...)  
{  
    int nSize = 0;  
    char buff[BUFFCOUNT];  
    memset(buff, 0, sizeof(buff));  
    va_list args;  
    va_start(args, formatstring);  
    nSize = vsnprintf(buff, sizeof(buff), formatstring, args);  
    printf("nSize: %d, buff: %s\n", nSize, buff);  
}  
  
int main() {  
    FormatOutput("%s %s", "Hi", "there");   //  8 chars + null  
    FormatOutput("%s %s", "Hi", "there!");  //  9 chars + null  
    FormatOutput("%s %s", "Hi", "there!!"); // 10 chars + null  
}  
```  
  
```Output  
nSize: 8 受惠於所加持︰ 大家有 nSize: 9 受惠於所加持︰ 大家那里 ！nSize: 10、 受惠於所加持︰ 大家那里 ！  
```  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [vprintf 函式](../../c-runtime-library/vprintf-functions.md)   
 [格式規格語法：printf 和 wprintf 函式](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)   
 [fprintf、\_fprintf\_l、fwprintf、\_fwprintf\_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf、\_printf\_l、wprintf、\_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf、\_sprintf\_l、swprintf、\_swprintf\_l、\_\_swprintf\_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [va\_arg、va\_copy、va\_end、va\_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)