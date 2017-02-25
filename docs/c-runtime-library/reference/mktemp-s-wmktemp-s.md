---
title: "_mktemp_s、_wmktemp_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mktemp_s"
  - "_wmktemp_s"
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
  - "wmktemp_s"
  - "mktemp_s"
  - "_mktemp_s"
  - "_wmktemp_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mktemp_s 函式"
  - "_tmktemp_s 函式"
  - "_wmktemp_s 函式"
  - "檔案 [C++], 暫存"
  - "mktemp_s 函式"
  - "暫存檔案 [C++]"
  - "tmktemp_s 函式"
  - "wmktemp_s 函式"
ms.assetid: 92a7e269-7f3d-4c71-bad6-14bc827a451d
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# _mktemp_s、_wmktemp_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

建立唯一的檔案名稱。  這些是 [\_mktemp、\_wmktemp](../../c-runtime-library/reference/mktemp-wmktemp.md) 的安全性增強版本，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
## 語法  
  
```  
errno_t _mktemp_s(  
   char *template,  
   size_t sizeInChars  
);  
errno_t _wmktemp_s(  
   wchar_t *template,  
   size_t sizeInChars  
);  
template <size_t size>  
errno_t _mktemp_s(  
   char (&template)[size]  
); // C++ only  
template <size_t size>  
errno_t _wmktemp_s(  
   wchar_t (&template)[size]  
); // C++ only  
```  
  
#### 參數  
 `template`  
 檔名模式。  
  
 `sizeInChars`  
 緩衝區的大小 \(以單一位元組字元的 `_mktemp_s`中;在 `_wmktemp_s`的寬字元，包括 null 結束字元。  
  
## 傳回值  
 在成功這兩個函式會傳回零;在失敗時的錯誤碼。  
  
### 錯誤狀況  
  
|`template`|`sizeInChars`|**傳回值**|**在範本的新值。**|  
|----------------|-------------------|-------------|-----------------|  
|`NULL`|any|`EINVAL`|`NULL`|  
|無效的格式 \(如果參數參考之 `Remarks` 區段\)|any|`EINVAL`|空字串|  
|any|\<\= X的數目。|`EINVAL`|空字串|  
  
 如果以上任何一個錯誤情況發生，無效的參數叫用處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，這些函式會將 `errno` 設為 `EINVAL`，而函式傳回`EINVAL`。  
  
## 備註  
 `_mktemp_s` 函式會修改 `template` 引數建立唯一的檔案名稱，，因此，在呼叫，其中包含新的檔案名稱後的字串的 `template` 指標。  `_mktemp_s` 適時地自動處理多位元組字元字串參數，根據目前執行階段系統中的多位元組字碼頁來辨認多位元組字元序列。  `_wmktemp_s` 是 `_mktemp_s` 的寬字元版本；`_wmktemp_s` 的引數是寬字元字串。  `_wmktemp_s` 和 `_mktemp_s` 行為相同，除了 `_wmktemp_s` 不處理多位元組字元字串。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE and \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|------------------------------|----------------|-------------------|  
|`_tmktemp_s`|`_mktemp_s`|`_mktemp_s`|`_wmktemp_s`|  
  
 `template` 參數的形式為 `baseXXXXXX`，其中 `base` 是您提供的新檔名的一部分，而每個 X 代表 `_mktemp_s` 提供的占位符字元。  每個在 `template` 中的占位符字元必須是大寫字母 X 。  `_mktemp_s` 保留 `base` 並以一個字母字元取代第一個結尾的 X 。  `_mktemp_s` 以一個五位數值取代接下來的末尾 X ，此值是一個唯一的代表呼叫處理程序的數字，或在多執行緒的應用程式裏代表呼叫執行緒。  
  
 每次成功地呼叫 `_mktemp_s` 都會修改 `template` 。  同一個處理程序或執行緒接下來每次以相同的 `template` 呼叫`_mktemp_s` 時，它會檢查檔案名稱是否與前一次呼叫 `_mktemp_s` 所回傳的名字相符。  如果給定的名字不存在， `_mktemp_s` 回傳相同的名字。  如果每一個前次回傳的名字的檔案都存在， `_mktemp_s` 會透過將之前回傳的名字中的字母字元取代為下一個小寫字母，以 a 到 z 的順序。  例如，當 `base` 是：  
  
```  
fn  
```  
  
 而由 `_mktemp_s` 提供的五位數字是 12345，則第一個回傳的名字是：  
  
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
  
 對於任何給定的基底與樣板值組合 `_mktemp_s` 可以建立最多 26 個唯一的檔案名稱。  因此，在這個例子裏， FNZ12345 是最後一個 `_mktemp_s` 可以為 `base` 和 `template` 值來建立的唯一檔名。  
  
 C\+\+ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 \(因而不須指定大小引數\)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。  如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_mktemp_s`|\<io.h\>|  
|`_wmktemp_s`|\<io.h\> or \<wchar.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 範例  
  
```  
// crt_mktemp_s.cpp  
/* The program uses _mktemp to create  
 * five unique filenames. It opens each filename  
 * to ensure that the next name is unique.  
 */  
  
#include <io.h>  
#include <string.h>  
#include <stdio.h>  
  
char *fnTemplate = "fnXXXXXX";  
char names[5][9];  
  
int main()  
{  
   int i, err, sizeInChars;  
   FILE *fp;  
  
   for( i = 0; i < 5; i++ )  
   {  
      strcpy_s( names[i], sizeof(names[i]), fnTemplate );  
      /* Get the size of the string and add one for the null terminator.*/  
      sizeInChars = strnlen(names[i], 9) + 1;  
      /* Attempt to find a unique filename: */  
      err = _mktemp_s( names[i], sizeInChars );  
      if( err != 0 )  
         printf( "Problem creating the template" );  
      else  
      {  
         if( fopen_s( &fp, names[i], "w" ) == 0 )  
            printf( "Unique filename is %s\n", names[i] );  
         else  
            printf( "Cannot open %s\n", names[i] );  
         fclose( fp );  
      }  
   }  
  
   return 0;  
}  
```  
  
## 範例輸出  
  
```  
Unique filename is fna03188  
Unique filename is fnb03188  
Unique filename is fnc03188  
Unique filename is fnd03188  
Unique filename is fne03188  
```  
  
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
 [tmpfile\_s](../../c-runtime-library/reference/tmpfile-s.md)