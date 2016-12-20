---
title: "gets_s、_getws_s | Microsoft Docs"
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
  - "_getws_s"
  - "gets_s"
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
  - "_getws_s"
  - "gets_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_getws_s 函式"
  - "緩衝區滿溢"
  - "緩衝區, 避免滿溢"
  - "緩衝區, 緩衝區滿溢"
  - "gets_s 函式"
  - "getws_s 函式"
  - "線條, 取得"
  - "標準輸入, 讀取自"
  - "資料流, 取得行"
ms.assetid: 5880c36f-122c-4061-a1a5-aeeced6fe58c
caps.latest.revision: 29
caps.handback.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# gets_s、_getws_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

從 `stdin` 資料流會取得一行。  這些 [gets, \_getws](../../c-runtime-library/gets-getws.md) 版本有安全性增強功能，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
## 語法  
  
```  
char *gets_s(   
   char *buffer,  
   size_t sizeInCharacters  
);  
wchar_t *_getws_s(   
   wchar_t *buffer,  
   size_t sizeInCharacters  
);  
template <size_t size>  
char *gets_s(   
   char (&buffer)[size]  
); // C++ only  
template <size_t size>  
wchar_t *_getws_s(   
   wchar_t (&buffer)[size]  
); // C++ only  
```  
  
#### 參數  
 \[out\] `buffer`  
 輸入字串的儲存位置。  
  
 \[in\] `sizeInCharacters`  
 緩衝區的大小。  
  
## 傳回值  
 如果成功，會傳回 `buffer`。  `NULL` 指標表示一個錯誤或文件關閉條件。  使用 [ferror](../../c-runtime-library/reference/ferror.md) 或 [feof](../../c-runtime-library/reference/feof.md) 來判斷哪時發生。  
  
## 備註  
 `gets_s` 函式。 會從標準輸入資料流 `stdin` 的一行並儲存它在`buffer`。  此行包括所有字元一直到第一個新行字元 \(「\\ n」\)。  `gets_s` 是在傳回前一行 null 字元 \(「\\ 0 」\) 取代之新行字元。  相反地， `fgets_s` 函式會將新行字元。  
  
 如果第一個字元是讀取檔案結尾字元， null 字元在 `buffer` 前端儲存，且會傳回 `NULL` 。  
  
 `_getws` 是 `gets_s` 的寬字元版本；函式的引數和回傳值是寬字元字串。  
  
 如果 `buffer` 是 `NULL` 或 `sizeInCharacters` 小於或等於零，或者，如果緩衝區太小無法包含匯出入列和 null 結束字元，這些函式會叫用無效的參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，這些函式會傳回 `NULL`，並將 `ERANGE` 設為 errno。  
  
 C\+\+ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 \(因而不須指定大小引數\)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。  如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_getts`|`gets_s`|`gets_s`|`_getws`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`gets_s`|\<stdio.h\>|  
|`_getws`|\<stdio.h\> 或 \<wchar.h\>|  
  
 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式不支援主控台。  與主控台關聯的標準資料流控制代碼 \(`stdin`、`stdout` 和 `stderr`\) 必須重新導向，然後 C 執行階段函式才能在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式中使用它們。  如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_gets_s.c  
// This program retrieves a string from the stdin and   
// prints the same string to the console.  
  
#include <stdio.h>  
  
int main( void )  
{  
   char line[21]; // room for 20 chars + '\0'  
   gets_s( line, 20 );  
   printf( "The line entered was: %s\n", line );  
}  
```  
  
  **`Hello there!`The line entered was: Hello there\!**   
## .NET Framework 對等用法  
 [System::Console::Read](https://msdn.microsoft.com/en-us/library/system.console.read.aspx)  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [gets、\_getws](../../c-runtime-library/gets-getws.md)   
 [fgets、fgetws](../../c-runtime-library/reference/fgets-fgetws.md)   
 [fputs、fputws](../../c-runtime-library/reference/fputs-fputws.md)   
 [puts、\_putws](../../c-runtime-library/reference/puts-putws.md)