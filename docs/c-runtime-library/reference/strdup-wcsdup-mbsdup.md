---
title: "_strdup、_wcsdup、_mbsdup | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_strdup"
  - "_mbsdup"
  - "_wcsdup"
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
  - "api-ms-win-crt-multibyte-l1-1-0.dll"
  - "api-ms-win-crt-string-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_tcsdup"
  - "mbsdup"
  - "_mbsdup"
  - "_strdup"
  - "_ftcsdup"
  - "_wcsdup"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "wcsdup 函式"
  - "ftcsdup 函式"
  - "_ftcsdup 函式"
  - "mbsdup 函式"
  - "strdup 函式"
  - "_strdup 函式"
  - "_wcsdup 函式"
  - "複製字串"
  - "重複字串"
  - "複製字串 [c + +]"
  - "_mbsdup 函式"
  - "複製字串 [c + +]"
  - "tcsdup 函式"
  - "_tcsdup 函式"
ms.assetid: 8604f8bb-95e9-45d3-93ef-20397ebf247a
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _strdup、_wcsdup、_mbsdup
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

重複字串。  
  
> [!IMPORTANT]
>  不可在於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 中執行的應用程式中使用 `_mbsdup`。 如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
char *_strdup(  
   const char *strSource   
);  
wchar_t *_wcsdup(  
   const wchar_t *strSource   
);  
unsigned char *_mbsdup(  
   const unsigned char *strSource   
);  
```  
  
#### 參數  
 `strSource`  
 以 Null 結束的來源字串。  
  
## 傳回值  
 這些函式全都會傳回所複製字串之儲存位置的指標，或是在無法配置儲存區時，傳回 `NULL`。  
  
## 備註  
 `_strdup` 函式呼叫 [malloc](../../c-runtime-library/reference/malloc.md) 來配置 `strSource` 複本的儲存空間，然後將 `strSource` 複製到配置的空間。  
  
 `_wcsdup` 和 `_mbsdup` 是寬字元和多位元組字元版本的 `_strdup`。`_wcsdup` 的引數和傳回值是寬字元字串；`_mbsdup` 的引數和傳回值則是多位元組字元字串。 除此之外，這三個函式的行為相同。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE 和 \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsdup`|`_strdup`|`_mbsdup`|`_wcsdup`|  
  
 因為 `_strdup` 呼叫 `malloc` 來配置 `strSource` 複本的儲存空間，所以一律在由 `_strdup` 的呼叫所傳回的指標上呼叫 [free](../../c-runtime-library/reference/free.md) 常式以釋放這個記憶體，是較好的做法。  
  
 如果已定義 `_DEBUG` 和 `_CRTDBG_MAP_ALLOC`，則 `_strdup` 和 `_wcsdup` 會由 `_strdup_dbg` 和 `_wcsdup_dbg` 的呼叫所取代，以便對記憶體配置進行偵錯。 如需詳細資訊，請參閱 [\_strdup\_dbg、\_wcsdup\_dbg](../../c-runtime-library/reference/strdup-dbg-wcsdup-dbg.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_strdup`|\<string.h\>|  
|`_wcsdup`|\<string.h\> 或 \<wchar.h\>|  
|`_mbsdup`|\<mbstring.h\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_strdup.c  
  
#include <string.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char buffer[] = "This is the buffer text";  
   char *newstring;  
   printf( "Original: %s\n", buffer );  
   newstring = _strdup( buffer );  
   printf( "Copy:     %s\n", newstring );  
   free( newstring );  
}  
```  
  
```Output  
Original: This is the buffer text Copy:     This is the buffer text  
```  
  
## .NET Framework 對等用法  
 [System::String::Clone](https://msdn.microsoft.com/en-us/library/system.string.clone.aspx)  
  
## 請參閱  
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [memset、wmemset](../../c-runtime-library/reference/memset-wmemset.md)   
 [strcat、wcscat、\_mbscat](../../c-runtime-library/reference/strcat-wcscat-mbscat.md)   
 [strcmp、wcscmp、\_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strncat、\_strncat\_l、wcsncat、\_wcsncat\_l、\_mbsncat、\_mbsncat\_l](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)   
 [strncmp、wcsncmp、\_mbsncmp、\_mbsncmp\_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [strncpy、\_strncpy\_l、wcsncpy、\_wcsncpy\_l、\_mbsncpy、\_mbsncpy\_l](../../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)   
 [\_strnicmp、\_wcsnicmp、\_mbsnicmp、\_strnicmp\_l、\_wcsnicmp\_l、\_mbsnicmp\_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr、wcsrchr、\_mbsrchr、\_mbsrchr\_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [strspn、wcsspn、\_mbsspn、\_mbsspn\_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)