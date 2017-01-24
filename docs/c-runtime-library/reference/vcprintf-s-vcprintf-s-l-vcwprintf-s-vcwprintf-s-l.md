---
title: "_vcprintf_s、_vcprintf_s_l、_vcwprintf_s、_vcwprintf_s_l | Microsoft Docs"
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
  - "_vcprintf_s"
  - "_vcprintf_s_l"
  - "_vcwprintf_s"
  - "_vcwprintf_s_l"
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
  - "vcprintf_s"
  - "vcwprintf_s_l"
  - "_vcwprintf_s"
  - "_vcwprintf_s_l"
  - "_vcprintf_s_l"
  - "_vtcprintf_s"
  - "vcwprintf_s"
  - "vcprintf_s_l"
  - "_vcprintf_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_vcprintf_s 函式"
  - "_vcprintf_s_l 函式"
  - "_vcwprintf_s 函式"
  - "_vcwprintf_s_l 函式"
  - "_vtcprintf_s 函式"
  - "_vtcprintf_s_l 函式"
  - "格式化的文字 [C++]"
  - "vcprintf_s 函式"
  - "vcprintf_s_l 函式"
  - "vcwprintf_s 函式"
  - "vcwprintf_s_l 函式"
  - "vtcprintf_s 函式"
  - "vtcprintf_s_l 函式"
ms.assetid: 5a46d45a-30db-45df-9850-455cbdac5636
caps.latest.revision: 24
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _vcprintf_s、_vcprintf_s_l、_vcwprintf_s、_vcwprintf_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用引數清單的指標將格式化輸出寫入至主控台。  這些 [\_vcprintf、\_vcprintf\_l、\_vcwprintf、\_vcwprintf\_l](../../c-runtime-library/reference/vcprintf-vcprintf-l-vcwprintf-vcwprintf-l.md) 版本有安全性增強功能，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
int _vcprintf(  
   const char* format,  
   va_list argptr  
);  
int _vcprintf(  
   const char* format,  
   locale_t locale,  
   va_list argptr  
);  
int _vcwprintf_s(  
   const wchar_t* format,  
   va_list argptr  
);  
int _vcwprintf_s_l(  
   const wchar_t* format,  
   locale_t locale,  
   va_list argptr  
);  
```  
  
#### 參數  
 `format`  
 格式規範。  
  
 `argptr`  
 指向引數清單的指標。  
  
 `locale`  
 使用的地區設定。  
  
 如需詳細資訊，請參閱[格式規格語法：printf 和 wprintf 函式](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。  
  
## 傳回值  
 列印的字元數，但當其為負值時，表示輸出發生錯誤。  
  
 像是這類函式的較不安全版本，如果 `format` 為 null 指標，則叫用無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  此外，不同於這些函式的較不安全版本則為，如果 `format` 沒有指定有效格式，會產生無效的參數例外狀況。  如果執行允許繼續執行，這些函式會傳回錯誤碼並將 `errno` 設為該錯誤代碼。  如果特定值無法適用，其預設錯誤碼為 `EINVAL` 。  
  
## 備註  
 這些函式接受一個指向參數清單的指標，然後格式化並將給定的資料寫入至主控台。  `_vcwprintf_s` 是 `_vcprintf_s`的寬字元版本。  它會採用寬字元字串做為引數。  
  
 這些有 `_l` 尾碼的函式版本是一樣的，不同之處在於會使用傳入的地區設定，而不使用目前的地區設定。  
  
> [!IMPORTANT]
>  確認 `format` 不是使用者定義的字串。  如需詳細資訊，請參閱 [Avoiding Buffer Overruns](http://msdn.microsoft.com/library/windows/desktop/ms717795) 。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_vtcprintf_s`|`_vcprintf_s`|`_vcprintf_s`|`_vcwprintf_s`|  
|`_vtcprintf_s_l`|`_vcprintf_s_l`|`_vcprintf_s_l`|`_vcwprintf_s_l`|  
  
## 需求  
  
|常式|必要的標頭|選擇性的標頭檔|  
|--------|-----------|-------------|  
|`_vcprintf_s`, `_vcprintf_s_l`|\<conio.h\> 和 \<stdarg.h\>|\<varargs.h\>\*|  
|`_vcwprintf_s`, `_vcwprintf_s_l`|\<conio.h\> 或 \<wchar.h\>，以及 \<stdarg.h\>|\<varargs.h\>\*|  
  
 \* 要求 UNIX V 相容性。  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_vcprintf_s.cpp  
#include <conio.h>  
#include <stdarg.h>  
  
// An error formatting function used to print to the console.  
int eprintf_s(const char* format, ...)  
{  
  va_list args;  
  va_start(args, format);  
  return _vcprintf_s(format, args);  
}  
  
int main()  
{  
   eprintf_s("  (%d:%d): Error %s%d : %s\n", 10, 23, "C", 2111,  
           "<some error text>");  
   eprintf_s("  (Related to symbol '%s' defined on line %d).\n",  
           "<symbol>", 5 );  
}  
```  
  
  **\(10,23\): Error C2111 : \<some error text\>**  
 **\(與第5行定義的\<symbol\>' 符號相關\).**   
## .NET Framework 對等用法  
 [System::Console::Write](https://msdn.microsoft.com/en-us/library/system.console.write.aspx)  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [vprintf 函式](../../c-runtime-library/vprintf-functions.md)   
 [\_cprintf、\_cprintf\_l、\_cwprintf、\_cwprintf\_l](../../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)   
 [fprintf、\_fprintf\_l、fwprintf、\_fwprintf\_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf、\_printf\_l、wprintf、\_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf、\_sprintf\_l、swprintf、\_swprintf\_l、\_\_swprintf\_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [va\_arg、va\_copy、va\_end、va\_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)