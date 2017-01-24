---
title: "_mktemp、_wmktemp | Microsoft Docs"
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
  - "_wmktemp"
  - "_mktemp"
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
  - "_tmktemp"
  - "wmktemp"
  - "tmktemp"
  - "_wmktemp"
  - "_mktemp"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_mktemp 函式"
  - "_tmktemp 函式"
  - "_wmktemp 函式"
  - "檔案 [C++], 暫存"
  - "mktemp 函式"
  - "暫存檔案 [C++]"
  - "tmktemp 函式"
  - "wmktemp 函式"
ms.assetid: 055eb539-a8c2-4a7d-be54-f5b6d1eb5c85
caps.latest.revision: 25
caps.handback.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _mktemp、_wmktemp
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

建立唯一的檔案名稱。  這些函式已有更安全的版本可用，請參閱 [\_mktemp\_s、\_wmktemp\_s](../../c-runtime-library/reference/mktemp-s-wmktemp-s.md)。  
  
## 語法  
  
```  
char *_mktemp(  
   char *template   
);  
wchar_t *_wmktemp(  
   wchar_t *template   
);  
template <size_t size>  
char *_mktemp(  
   char (&template)[size]  
); // C++ only  
template <size_t size>  
wchar_t *_wmktemp(  
   wchar_t (&template)[size]  
); // C++ only  
```  
  
#### 參數  
 `template`  
 檔名模式。  
  
## 傳回值  
 這些函式每一個都會回傳指向已修改的樣板的指標。  如果 `template` 的格式不正確或已經無法從給定的樣板中產生新的唯一名稱，函式將會回傳 `NULL` 。  
  
## 備註  
 `_mktemp` 函式透過修改 `template` 參數建立新的唯一檔名。  `_mktemp` 適時地自動處理多位元組字元字串參數，根據目前執行階段系統中的多位元組字碼頁來辨認多位元組字元序列。  `_wmktemp` 是 `_mktemp` 的寬字元版本，`_wmktemp` 函式的參數和回傳值是寬字元字串。  `_wmktemp` 和 `_mktemp` 行為相同，除了 `_wmktemp` 不處理多位元組字元字串。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE and \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|------------------------------|----------------|-------------------|  
|`_tmktemp`|`_mktemp`|`_mktemp`|`_wmktemp`|  
  
 `template` 參數的形式為 `base`XXXXXX，其中 `base` 是您提供的新檔名的一部分，而每個 X 代表 `_mktemp` 提供的占位符字元。  每個在 `template` 中的占位符字元必須是大寫字母 X 。  `_mktemp` 保留 `base` 並以一個字母字元取代第一個結尾的 X 。  `_mktemp` 以一個五位數值取代接下來的末尾 X ，此值是一個唯一的代表呼叫處理程序的數字，或在多執行緒的應用程式裏代表呼叫執行緒。  
  
 每次成功地呼叫  `_mktemp` 都會修改 `template` 。  同一個處理程序或執行緒接下來每次以相同的 `template` 呼叫`_mktemp` 時，它會檢查檔案名稱是否與前一次呼叫 `_mktemp` 所回傳的名字相符。  如果給定的名字不存在， `_mktemp` 回傳相同的名字。  如果每一個前次回傳的名字的檔案都存在， `_mktemp` 會透過將之前回傳的名字中的字母字元取代為下一個小寫字母，以 a 到 z 的順序。  例如，當 `base` 是：  
  
```  
fn  
```  
  
 而由 `_mktemp` 提供的五位數字是 12345，則第一個回傳的名字是：  
  
```  
fna12345  
```  
  
 如果這個名稱用來建立檔案 FNA12345 而這個檔案仍存在，下一次同一個處理程序和執行緒以同樣的 `base` 所回傳給 `template` 的名字是：  
  
```  
fnb12345  
```  
  
 如果 FNA12345 不存在，則傳回的會是：  
  
```  
fna12345  
```  
  
 對於任何給定的基底與樣板值組合 `_mktemp` 可以建立最多 26 個唯一的檔案名稱。  因此，在這個例子裏， FNZ12345 是最後一個 `_mktemp` 可以為 `base` 和 `template` 值來建立的唯一檔名。  
  
 在錯誤發生時， `errno` 會被設置。  如果 `template` 的格式無效 \(例如，小於 6 個 X\) ， `errno` 會被設為 `EINVAL` 。  如果 `_mktemp` 因為所有 26 個可能的檔案名稱均已經存在而無法建立唯一的名稱， `_mktemp` 設定樣板為空字串並回傳 `EEXIST` 。  
  
 在 C\+\+ 中，這些函式具有多載樣板，可以叫用更新、更安全的這些函式的相對版本。  如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_mktemp`|\<io.h\>|  
|`_wmktemp`|\<io.h\> or \<wchar.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 範例  
  
```  
// crt_mktemp.c  
// compile with: /W3  
/* The program uses _mktemp to create  
 * unique filenames. It opens each filename  
 * to ensure that the next name is unique.  
 */  
  
#include <io.h>  
#include <string.h>  
#include <stdio.h>  
#include <errno.h>  
  
char *template = "fnXXXXXX";  
char *result;  
char names[27][9];  
  
int main( void )  
{  
   int i;  
   FILE *fp;  
  
   for( i = 0; i < 27; i++ )  
   {  
      strcpy_s( names[i], sizeof( names[i] ), template );  
      /* Attempt to find a unique filename: */  
      result = _mktemp( names[i] );  // C4996  
      // Note: _mktemp is deprecated; consider using _mktemp_s instead  
      if( result == NULL )  
      {  
         printf( "Problem creating the template\n" );  
         if (errno == EINVAL)  
         {  
             printf( "Bad parameter\n");  
         }  
         else if (errno == EEXIST)  
         {  
             printf( "Out of unique filenames\n");   
         }  
      }  
      else  
      {  
         fopen_s( &fp, result, "w" );  
         if( fp != NULL )  
            printf( "Unique filename is %s\n", result );  
         else  
            printf( "Cannot open %s\n", result );  
         fclose( fp );  
      }  
   }  
}  
```  
  
  **Unique filename is fna03912**  
**Unique filename is fnb03912**  
**Unique filename is fnc03912**  
**Unique filename is fnd03912**  
**Unique filename is fne03912**  
**Unique filename is fnf03912**  
**Unique filename is fng03912**  
**Unique filename is fnh03912**  
**Unique filename is fni03912**  
**Unique filename is fnj03912**  
**Unique filename is fnk03912**  
**Unique filename is fnl03912**  
**Unique filename is fnm03912**  
**Unique filename is fnn03912**  
**Unique filename is fno03912**  
**Unique filename is fnp03912**  
**Unique filename is fnq03912**  
**Unique filename is fnr03912**  
**Unique filename is fns03912**  
**Unique filename is fnt03912**  
**Unique filename is fnu03912**  
**Unique filename is fnv03912**  
**Unique filename is fnw03912**  
**Unique filename is fnx03912**  
**Unique filename is fny03912**  
**Unique filename is fnz03912**  
**問題建立樣板**  
**Out of unique filenames.**   
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [檔案處理](../../c-runtime-library/file-handling.md)   
 [fopen、\_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [\_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [\_getpid](../../c-runtime-library/reference/getpid.md)   
 [\_open、\_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [\_setmbcp](../../c-runtime-library/reference/setmbcp.md)   
 [\_tempnam、\_wtempnam、tmpnam、\_wtmpnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)   
 [tmpfile](../../c-runtime-library/reference/tmpfile.md)