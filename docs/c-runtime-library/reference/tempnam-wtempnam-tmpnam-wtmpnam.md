---
title: "_tempnam、_wtempnam、tmpnam、_wtmpnam | Microsoft Docs"
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
  - "_wtempnam"
  - "_wtmpnam"
  - "tmpnam"
  - "_tempnam"
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
  - "wtempnam"
  - "_wtmpnam"
  - "wtmpnam"
  - "tmpnam"
  - "_wtempnam"
  - "_tempnam"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_tempnam 函式"
  - "_ttmpnam 函式"
  - "_wtempnam 函式"
  - "_wtmpnam 函式"
  - "檔案名稱 [C++], 建立暫存"
  - "檔案名稱 [C++], 暫存"
  - "tempnam 函式"
  - "暫存檔案, 建立"
  - "tmpnam 函式"
  - "ttmpnam 函式"
  - "wtempnam 函式"
  - "wtmpnam 函式"
ms.assetid: 3ce75f0f-5e30-42a6-9791-8d7cbfe70fca
caps.latest.revision: 20
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _tempnam、_wtempnam、tmpnam、_wtmpnam
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

產生您可以使用於建立暫存檔的名稱。  其中部分函式的可用安全版本，請參閱 [tmpnam\_s、\_wtmpnam\_s](../../c-runtime-library/reference/tmpnam-s-wtmpnam-s.md)。  
  
## 語法  
  
```  
char *_tempnam(  
   const char *dir,  
   const char *prefix   
);  
wchar_t *_wtempnam(  
   const wchar_t *dir,  
   const wchar_t *prefix   
);  
char *tmpnam(  
   char *str   
);  
wchar_t *_wtmpnam(  
   wchar_t *str   
);  
```  
  
#### 參數  
 `prefix`  
 將會附加到名稱的字串是由 `_tempnam`傳回。  
  
 `dir`  
 如果沒有 TMP 環境變數，或者如果 TMP 不是有效的目錄，路徑用於檔案名稱。  
  
 `str`  
 將保留產生名稱的指標，且與使用函式傳回的名稱是相同的。  這是很方便儲存產生的名稱的方法。  
  
## 傳回值  
 如果發生失敗，這些函式都會傳回指向產生的名稱或 `NULL` 的指標。  如果您想要更多具有 `tmpnam` 的 `TMP_MAX`\(參閱 STDIO.H\) 呼叫或是如果您使用 `_tempnam` 且在 TMP 環境變數中及 `dir` 中有指定無效的目錄名稱，可能會發生失敗。  
  
> [!NOTE]
>  指標是由 `tmpnam` 和 `_wtmpnam` 傳回至內部靜態緩衝區。  不應該呼叫[可用](../../c-runtime-library/reference/free.md) 取消這些指標。  `free` 必須為 `_tempnam` 和 `_wtempnam`配置的指標來呼叫。  
  
## 備註  
 這些函式都會傳回目前不存在的檔名。  `tmpnam` 傳回在工作目錄唯一名稱且 `_tempnam` 讓您在目錄中產生不同於目前的唯一名稱。  請注意，會在檔名之前加上反斜線且沒有路徑資訊，例如\\ fname21，這表示這名稱在目前工作目錄是有效的。  
  
 如果是 `tmpnam`，則可在 `str` 中儲存這個產生的檔案名稱。  如果 `str` 是 `NULL`，那麼 `tmpnam` 將結果留在內部靜態緩衝區。  因此所有後續的呼叫會摧毀此值。  `tmpnam` 產生的檔名包含程式產生的檔案名稱，而且，在第一次呼叫 `tmpnam` 之後，基底為 32 的副檔名序號為 \(.1\-.1vvu，當 STDIO.H 的 `TMP_MAX` 是 32,767\)。  
  
 `_tempnam` 會為目錄產生唯一的檔案名稱依下列規則選取：  
  
-   如果 TMP 環境變數定義並設定為有效的目錄名稱，唯一的檔案名稱為 TMP 指定的目錄中產生。  
  
-   如果 TMP 環境變數未定義，或者設定為不存在的目錄名稱， `_tempnam` 會使用 `dir` 參數做為它將產生唯一名稱的路徑。  
  
-   如果 TMP 環境變數未定義，或者設定為不存在的目錄名稱，且如果 `dir` 為 `NULL` ，或設定為不存在的目錄名稱， `_tempnam` 會使用目前工作目錄產生唯一的名稱。  目前，如果 TMP 和 `dir` 皆指定不存在的目錄名稱， `_tempnam` 函式呼叫將會失敗。  
  
 `_tempnam` 傳回的名稱將是 `prefix` 和序號的連接，該名稱將合併建立唯一名稱指定的目錄。  `_tempnam` 產生沒有副檔名的檔案名稱。  `_tempnam` 使用 [malloc](../../c-runtime-library/reference/malloc.md) 配置這個檔名的空間;，當不再需要時，程式會負責釋放這個空間。  
  
 `_tempnam` 和 `tmpnam` 會根據從作業系統取得的 OEM 字碼頁自動適當地處理多位元組字串，辨識多位元組序列。  `_wtempnam` 是 `_tempnam` 的寬字元版本；`_wtempnam` 的引數和回傳值是寬字元字串。  `_wtempnam` 和 `_tempnam` 行為相同，除了 `_wtempnam` 不處理多位元組字元字串。  `_wtmpnam` 是 `tmpnam` 的寬字元版本，`_wtmpnam` 函式的參數和回傳值是寬字元字串。  `_wtmpnam` 和 `tmpnam` 行為相同，除了 `_wtmpnam` 不處理多位元組字元字串。  
  
 如果 `_DEBUG` 和 `_CRTDBG_MAP_ALLOC` 已定義 `_tempnam` 和 `_wtempnam` 由 [\_tempnam\_dbg 和 \_wtempnam\_dbg](../../c-runtime-library/reference/tempnam-dbg-wtempnam-dbg.md)的呼叫取代。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|\_UNICODE & \_MBCS 未定義|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_ttmpnam`|`tmpnam`|`tmpnam`|`_wtmpnam`|  
|`_ttempnam`|`_tempnam`|`_tempnam`|`_wtempnam`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_tempnam`|\<stdio.h\>|  
|`_wtempnam`, `_wtmpnam`|\<stdio.h\> 或 \<wchar.h\>|  
|`tmpnam`|\<stdio.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_tempnam.c  
// compile with: /W3  
// This program uses tmpnam to create a unique filename in the  
// current working directory, then uses _tempnam to create   
// a unique filename with a prefix of stq.   
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{     
   char* name1 = NULL;  
   char* name2 = NULL;  
  
   // Create a temporary filename for the current working directory:   
   if( ( name1 = tmpnam( NULL ) ) != NULL ) // C4996  
   // Note: tmpnam is deprecated; consider using tmpnam_s instead  
      printf( "%s is safe to use as a temporary file.\n", name1 );  
   else  
      printf( "Cannot create a unique filename\n" );  
  
   // Create a temporary filename in temporary directory with the  
   // prefix "stq". The actual destination directory may vary  
   // depending on the state of the TMP environment variable and  
   // the global variable P_tmpdir.     
  
   if( ( name2 = _tempnam( "c:\\tmp", "stq" ) ) != NULL )  
      printf( "%s is safe to use as a temporary file.\n", name2 );   
   else  
      printf( "Cannot create a unique filename\n" );  
  
   // When name2 is no longer needed :     
   if(name2)  
     free(name2);  
  
}  
```  
  
  **\\s1gk. is safe to use as a temporary file.**  
**C:\\DOCUME~1\\user\\LOCALS~1\\Temp\\2\\stq2 is safe to use as a temporary file.**   
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [\_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [\_setmbcp](../../c-runtime-library/reference/setmbcp.md)   
 [tmpfile](../../c-runtime-library/reference/tmpfile.md)   
 [tmpfile\_s](../../c-runtime-library/reference/tmpfile-s.md)