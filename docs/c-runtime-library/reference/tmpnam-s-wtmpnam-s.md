---
title: "tmpnam_s、_wtmpnam_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "tmpnam_s"
  - "_wtmpnam_s"
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
  - "tmpnam_s"
  - "_wtmpnam_s"
  - "L_tmpnam_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_wtmpnam_s 函式"
  - "檔案名稱 [C++], 建立暫存"
  - "檔案名稱 [C++], 暫存"
  - "L_tmpnam_s 常數"
  - "暫存檔案, 建立"
  - "tmpnam_s 函式"
  - "wtmpnam_s 函式"
ms.assetid: e70d76dc-49f5-4aee-bfa2-f1baa2bcd29f
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# tmpnam_s、_wtmpnam_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

產生您可以使用於建立暫存檔的名稱。  這些是 [tmpnam and \_wtmpnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md) 的安全性增強版本，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md) 中所述。  
  
## 語法  
  
```  
errno_t tmpnam_s(  
   char * str,  
   size_t sizeInChars   
);  
errno_t _wtmpnam_s(  
   wchar_t *str,  
   size_t sizeInChars   
);  
template <size_t size>  
errno_t tmpnam_s(  
   char (&str)[size]  
); // C++ only  
template <size_t size>  
errno_t _wtmpnam_s(  
   wchar_t (&str)[size]  
); // C++ only  
```  
  
#### 參數  
 \[out\] `str`  
 保留產生名稱的指標。  
  
 \[in\] `sizeInChars`  
 緩衝區的大小，以位元組為單位。  
  
## 傳回值  
 如果成功，這兩個函式傳回 0，失敗時則為錯誤代碼。  
  
### 錯誤狀況  
  
|||||  
|-|-|-|-|  
|`str`|`sizeInChars`|**傳回值**|`str` **的內容**|  
|`NULL`|any|`EINVAL`|未修改|  
|不是 `NULL` \(指向有效的記憶體\)|太短|`ERANGE`|未修改|  
  
 如果 `str` 是 `NULL`，則叫用無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，這些函式會將 `errno` 設定為 `EINVAL` 並傳回 `EINVAL`。  
  
## 備註  
 這些函式都會傳回目前不存在的檔名。  `tmpnam_s` 傳回在目前的工作目錄唯一的名稱。  請注意，會在檔名之前加上反斜線且沒有路徑資訊，例如\\ fname21，這表示這名稱在目前工作目錄是有效的。  
  
 如果是 `tmpnam_s`，則 `str`可以儲存這個產生的檔案名稱。  `tmpnam_s` 傳回之字串的最大長度是 `L_tmpnam_s`，定義在 STDIO.H。  如果 `str` 是 `NULL`，那麼 `tmpnam_s` 將結果留在內部靜態緩衝區。  因此所有後續的呼叫會摧毀此值。  `tmpnam_s` 產生的檔名包含程式產生的檔案名稱，而且，在第一次呼叫 `tmpnam_s` 之後，基底為 32 的副檔名序號為 \(.1\-.1vvvvvu，當 STDIO.H 的 `TMP_MAX_S` 是 INT\_MAX\)。  
  
 `tmpnam_s` 會根據從作業系統取得的 OEM 字碼頁自動處理多位元組字元字串引數為適當，可辨識的多位元組字元序列。  `_wtmpnam_s` 是 `tmpnam_s` 的寬字元版本，`_wtmpnam_s` 函式的參數和回傳值是寬字元字串。  `_wtmpnam_s` 和 `tmpnam_s` 行為相同，除了 `_wtmpnam_s` 不處理多位元組字元字串。  
  
 在 C\+\+ 中，這些函式的使用被簡化為使用樣板多載；使用多載可以自動推斷緩衝區的大小而不必在參數中指明大小。  如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|\_UNICODE 和 \_MBCS 未定義|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_ttmpnam_s`|`tmpnam_s`|`tmpnam_s`|`_wtmpnam_s`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`tmpnam_s`|\<stdio.h\>|  
|`_wtmpnam_s`|\<stdio.h\> 或 \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_tmpnam_s.c  
// This program uses tmpnam_s to create a unique filename in the  
// current working directory.   
//  
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{     
   char name1[L_tmpnam_s];  
   errno_t err;  
   int i;  
  
   for (i = 0; i < 15; i++)  
   {  
      err = tmpnam_s( name1, L_tmpnam_s );  
      if (err)  
      {  
         printf("Error occurred creating unique filename.\n");  
         exit(1);  
      }  
      else  
      {  
         printf( "%s is safe to use as a temporary file.\n", name1 );  
      }  
   }    
}  
```  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [\_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [\_setmbcp](../../c-runtime-library/reference/setmbcp.md)   
 [tmpfile\_s](../../c-runtime-library/reference/tmpfile-s.md)