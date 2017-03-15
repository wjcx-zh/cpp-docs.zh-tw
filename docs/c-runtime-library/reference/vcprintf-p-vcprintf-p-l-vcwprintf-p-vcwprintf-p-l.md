---
title: "_vcprintf_p、_vcprintf_p_l、_vcwprintf_p、_vcwprintf_p_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_vcprintf_p"
  - "_vcwprintf_p_l"
  - "_vcprintf_p_l"
  - "_vcwprintf_p"
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
  - "vcwprintf_p"
  - "vcprintf_p_l"
  - "_vcprintf_p"
  - "_vcprintf_p_l"
  - "vcwprintf_p_l"
  - "vcprintf_p"
  - "_vcwprintf_p"
  - "_vcwprintf_p_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_vcprintf_p 函式"
  - "_vcprintf_p_l 函式"
  - "_vcwprintf_p 函式"
  - "_vcwprintf_p_l 函式"
  - "_vtcprintf_p 函式"
  - "_vtcprintf_p_l 函式"
  - "vcprintf_p 函式"
  - "vcprintf_p_l 函式"
  - "vcwprintf_p 函式"
  - "vcwprintf_p_l 函式"
  - "vtcprintf_p 函式"
  - "vtcprintf_p_l 函式"
ms.assetid: 611024cc-90e7-41db-8e85-145ca95012b1
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# _vcprintf_p、_vcprintf_p_l、_vcwprintf_p、_vcwprintf_p_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用引數清單的指標將格式化輸出寫入到主控台，並支援在格式字串中的位置參數。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 中執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
int _vcprintf_p(  
   const char* format,  
   va_list argptr  
);  
int _vcprintf_p_l(  
   const char* format,  
   locale_t locale,  
   va_list argptr  
);  
int _vcwprintf_p(  
   const wchar_t* format,  
   va_list argptr  
);  
int _vcwprintf_p_l(  
   const wchar_t* format,  
   locale_t locale,  
   va_list argptr  
);  
```  
  
#### 參數  
 `format`  
 格式規格。  
  
 `argptr`  
 引數清單的指標。  
  
 `locale`  
 要使用的地區設定。  
  
 如需詳細資訊，請參閱[格式規格語法：printf 和 wprintf 函式](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。  
  
## 傳回值  
 寫入的字元數，或是當發生輸出錯誤時為負值。  如果 `format` 為 null 指標，則會叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，則 `errno` 會設定為 `EINVAL`，且會傳回 \-1。  
  
## 備註  
 這些函式中每一個都接受引數清單的指標，然後使用 `_putch` 函式將指定資料格式化和寫入主控台。  \(`_vcwprintf_p` 使用 `_putwch` 來取代 `_putch`。  `_vcwprintf_p` 是寬字元版本的 `_vcprintf_p`。  它需要寬字元字串做為引數。\)  
  
 這些有 `_l` 尾碼的函式版本都相同，不同之處在於會使用傳入的地區設定參數，而不使用目前的地區設定。  
  
 每個 `argument` \(如果有\) 皆根據 `format` 中的對應格式規格進行轉換和輸出。  格式規格支援位置參數，以便讓您可以指定格式字串中使用引數的順序。  如需詳細資訊，請參閱 [printf\_p 位置參數](../../c-runtime-library/printf-p-positional-parameters.md)。  
  
 在輸出換行字元時，這些函式不會將其轉譯為歸位字元\-換行字元 \(CR\-LF\) 組合。  
  
> [!IMPORTANT]
>  確認 `format` 不是使用者定義的字串。  如需詳細資訊，請參閱[避免緩衝區滿溢](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
 這些函式會驗證輸入的指標和格式字串。  如果 `format` 或 `argument` 為 `NULL`，或如果此格式字串包含無效格式化字元，則這些函式會叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，這些函式會傳回 \-1，並將 `errno` 設為 `EINVAL`。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE 和 \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_vtcprintf_p`|`_vcprintf_p`|`_vcprintf_p`|`_vcwprintf_p`|  
|`_vtcprintf_p_l`|`_vcprintf_p_l`|`_vcprintf_p_l`|`_vcwprintf_p_l`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_vcprintf_p`, `_vcprintf_p_l`|\<conio.h\> 和 \<stdarg.h\>|  
|`_vcwprintf_p`, `_vcwprintf_p_l`|\<conio.h\> 和 \<stdarg.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_vcprintf_p.c  
// compile with: /c  
#include <conio.h>  
#include <stdarg.h>  
  
// An error formatting function that's used to print to the console.  
int eprintf(const char* format, ...)  
{  
  va_list args;  
  va_start(args, format);  
  return _vcprintf_p(format, args);  
}  
  
int main()  
{  
   int n = eprintf("parameter 2 = %2$d; parameter 1 = %1$s\r\n",  
      "one", 222);  
   _cprintf_s("%d characters printed\r\n");  
}  
```  
  
  **parameter 2 \= 222；parameter 1 \= one**  
**已列印 38 個字元**   
## 請參閱  
 [主控台和連接埠 I\/O](../../c-runtime-library/console-and-port-i-o.md)   
 [\_cprintf、\_cprintf\_l、\_cwprintf、\_cwprintf\_l](../../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)   
 [va\_arg、va\_copy、va\_end、va\_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)   
 [printf\_p 位置參數](../../c-runtime-library/printf-p-positional-parameters.md)