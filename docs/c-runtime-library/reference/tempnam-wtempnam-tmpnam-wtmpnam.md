---
title: "_tempnam、_wtempnam、tmpnam、_wtmpnam | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _wtempnam
- _wtmpnam
- tmpnam
- _tempnam
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wtempnam
- _wtmpnam
- wtmpnam
- tmpnam
- _wtempnam
- _tempnam
dev_langs:
- C++
helpviewer_keywords:
- wtempnam function
- file names [C++], creating temporary
- _tempnam function
- ttmpnam function
- tmpnam function
- tempnam function
- wtmpnam function
- temporary files, creating
- file names [C++], temporary
- _ttmpnam function
- _wtmpnam function
- _wtempnam function
ms.assetid: 3ce75f0f-5e30-42a6-9791-8d7cbfe70fca
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 29b0f7f645bd23c04e9d9f31dc914e29f7a048cb
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="tempnam-wtempnam-tmpnam-wtmpnam"></a>_tempnam、_wtempnam、tmpnam、_wtmpnam
產生可用來建立暫存檔的名稱。 您現在已有這些函式當中某些更安全的版本可以使用，請參閱 [tmpnam_s、_wtmpnam_s](../../c-runtime-library/reference/tmpnam-s-wtmpnam-s.md)。  
  
## <a name="syntax"></a>語法  
  
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
  
#### <a name="parameters"></a>參數  
 `prefix`  
 此字串會加在 `_tempnam` 所傳回的名稱前面。  
  
 `dir`  
 若沒有 TMP 環境變數，或是 TMP 不是有效的目錄時，檔案名稱中所使用的路徑。  
  
 `str`  
 將保留所產生名稱，並且將與函式所傳回之名稱相同的指標。 這便於儲存產生的名稱。  
  
## <a name="return-value"></a>傳回值  
 若發生失敗，這些函式均會傳回產生之名稱的指標或 `NULL`。 如果您嘗試使用，就會發生失敗超過`TMP_MAX`（請參閱 STDIO。H） 呼叫`tmpnam`或如果您使用`_tempnam`，而且沒有指定在 TMP 環境變數和不正確的目錄名稱`dir`參數。  
  
> [!NOTE]
>  `tmpnam` 和 `_wtmpnam` 所傳回的指標指向內部靜態緩衝區。 不應呼叫 [free](../../c-runtime-library/reference/free.md) 來解除配置這些指標。 需要針對 `_tempnam` 和 `_wtempnam` 配置的指標呼叫 `free`。  
  
## <a name="remarks"></a>備註  
 這些函式均會傳回目前不存在的檔案名稱。 `tmpnam` 傳回在目前工作目錄中唯一的名稱，而 `_tempnam` 可讓您在非目前目錄的目錄中產生唯一的名稱。 請注意，當檔案名稱前面附加反斜線且沒有路徑資訊時，例如 \fname21，這表示名稱對於目前工作目錄有效。  
  
 對於 `tmpnam`，您可以將這個產生的檔案名稱儲存在 `str`。 如果 `str` 是 `NULL`，則 `tmpnam` 會將結果保持在內部靜態緩衝區中。 因此任何後續呼叫會終結這個值。 `tmpnam` 所產生的名稱包含程式所產生的檔案名稱，以及在第一次呼叫 `tmpnam` 之後，以 32 為基底的序號副檔名 (.1-.vvu，當 `TMP_MAX` 在 STDIO.H 中時是 32,767)。  
  
 `_tempnam` 會產生目錄的唯一檔案名稱，目錄是依照下列規則來選擇︰  
  
-   若已定義 TMP 環境變數，而且設定為有效的目錄名稱，則會針對 TMP 所指定的目錄產生唯一的檔案名稱。  
  
-   如果未定義 TMP 環境變數，或是它設定為不存在之目錄的名稱，則 `_tempnam` 將使用 `dir` 參數作為它將為其產生唯一名稱的路徑。  
  
-   如果未定義 TMP 環境變數，或是它設定為不存在之目錄的名稱，而且 `dir` 是 `NULL` 或設定為不存在之目錄的名稱，則 `_tempnam` 會使用目前的工作目錄來產生唯一的名稱。 目前，如果 TMP 和 `dir` 都指定不存在之目錄的名稱，`_tempnam` 函式呼叫將會失敗。  
  
 `_tempnam` 傳回的名稱會串連 `prefix` 和序號，它們相結合可以為指定目錄建立唯一的檔案名稱。 `_tempnam` 會產生沒有副檔名的檔案名稱。 `_tempnam` 使用 [malloc](../../c-runtime-library/reference/malloc.md) 來配置檔案名稱的空間，程式會負責在不再需要時釋放此空間。  
  
 `_tempnam` 和 `tmpnam` 會自動適當地處理多位元組字元字串引數，並根據從作業系統取得的 OEM 字碼頁辨識多位元組字元序列。 `_wtempnam` 是 `_tempnam` 的寬字元版本，`_wtempnam` 的引數與傳回值是寬字元字串。 `_wtempnam` 與 `_tempnam` 的運作方式完全相同，不同之處在於 `_wtempnam` 不會處理多位元組字元字串。 `_wtmpnam` 是 `tmpnam` 的寬字元版本，`_wtmpnam` 的引數與傳回值是寬字元字串。 `_wtmpnam` 與 `tmpnam` 的運作方式完全相同，不同之處在於 `_wtmpnam` 不會處理多位元組字元字串。  
  
 如果已定義 `_DEBUG` 和 `_CRTDBG_MAP_ALLOC`，`_tempnam` 和 `_wtempnam` 會取代為 [_tempnam_dbg 和 _wtempnam_dbg](../../c-runtime-library/reference/tempnam-dbg-wtempnam-dbg.md) 的呼叫。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_ttmpnam`|`tmpnam`|`tmpnam`|`_wtmpnam`|  
|`_ttempnam`|`_tempnam`|`_tempnam`|`_wtempnam`|  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`_tempnam`|\<stdio.h>|  
|`_wtempnam`, `_wtmpnam`|\<stdio.h> 或 \<wchar.h>|  
|`tmpnam`|\<stdio.h>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>範例  
  
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
  
```Output  
\s1gk. is safe to use as a temporary file.  
C:\DOCUME~1\user\LOCALS~1\Temp\2\stq2 is safe to use as a temporary file.  
```  
  
## <a name="see-also"></a>請參閱  
 [資料流 I/O](../../c-runtime-library/stream-i-o.md)   
 [_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [_setmbcp](../../c-runtime-library/reference/setmbcp.md)   
 [tmpfile](../../c-runtime-library/reference/tmpfile.md)   
 [tmpfile_s](../../c-runtime-library/reference/tmpfile-s.md)