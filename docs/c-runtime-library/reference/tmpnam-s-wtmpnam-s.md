---
title: "tmpnam_s、_wtmpnam_s | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- tmpnam_s
- _wtmpnam_s
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
- tmpnam_s
- _wtmpnam_s
- L_tmpnam_s
dev_langs:
- C++
helpviewer_keywords:
- tmpnam_s function
- file names [C++], creating temporary
- _wtmpnam_s function
- L_tmpnam_s constant
- temporary files, creating
- file names [C++], temporary
- wtmpnam_s function
ms.assetid: e70d76dc-49f5-4aee-bfa2-f1baa2bcd29f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 844da11b981b99d5fe69861c3198d0508857a1a5
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="tmpnams-wtmpnams"></a>tmpnam_s、_wtmpnam_s
產生可用來建立暫存檔的名稱。 這些是 [tmpnam 和 _wtmpnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md) 的版本，具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。  
  
## <a name="syntax"></a>語法  
  
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
  
#### <a name="parameters"></a>參數  
 [輸出] `str`  
 將保留所產生名稱的指標。  
  
 [輸入] `sizeInChars`  
 緩衝區的大小 (以字元為單位)。  
  
## <a name="return-value"></a>傳回值  
 這些函式成功時均會傳回 0，或在失敗時傳回錯誤號碼。  
  
### <a name="error-conditions"></a>錯誤狀況  
  
|||||  
|-|-|-|-|  
|`str`|`sizeInChars`|**傳回值**|`str` **的內容**。|  
|`NULL`|any|`EINVAL`|未修改|  
|非 `NULL` (指向有效的記憶體)|太短|`ERANGE`|未修改|  
  
 如果 `str` 為 `NULL`，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會將 `errno` 設為 `EINVAL`，並傳回 `EINVAL`。  
  
## <a name="remarks"></a>備註  
 這些函式均會傳回目前不存在的檔案名稱。 `tmpnam_s` 傳回在目前工作目錄中唯一的名稱。 請注意，當檔案名稱前面附加反斜線且沒有路徑資訊時，例如 \fname21，這表示名稱對於目前工作目錄有效。  
  
 對於 `tmpnam_s`，您可以將這個產生的檔案名稱儲存在 `str`。 `tmpnam_s` 所傳回的字串最大長度是 `L_tmpnam_s`，如 STDIO.H 中所定義。 如果 `str` 是 `NULL`，則 `tmpnam_s` 會將結果保持在內部靜態緩衝區中。 因此任何後續呼叫會終結這個值。 `tmpnam_s` 所產生的名稱包含程式所產生的檔案名稱，以及在第一次呼叫 `tmpnam_s` 之後，以 32 為基底的序號副檔名 (.1-.1vvvvvu，當 `TMP_MAX_S` 在 STDIO.H 中時是 INT_MAX)。  
  
 `tmpnam_s` 會自動適當地處理多位元組字元字串引數，並根據從作業系統取得的 OEM 字碼頁辨識多位元組字元序列。 `_wtmpnam_s` 是 `tmpnam_s` 的寬字元版本，`_wtmpnam_s` 的引數與傳回值是寬字元字串。 `_wtmpnam_s` 與 `tmpnam_s` 的運作方式完全相同，不同之處在於 `_wtmpnam_s` 不會處理多位元組字元字串。  
  
 在 C++ 中，使用這些函式已為範本多載簡化；多載可自動推斷緩衝區長度，因而不需要指定大小引數。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_ttmpnam_s`|`tmpnam_s`|`tmpnam_s`|`_wtmpnam_s`|  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`tmpnam_s`|\<stdio.h>|  
|`_wtmpnam_s`|\<stdio.h> 或 \<wchar.h>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>範例  
  
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
  
## <a name="see-also"></a>請參閱  
 [資料流 I/O](../../c-runtime-library/stream-i-o.md)   
 [_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [_setmbcp](../../c-runtime-library/reference/setmbcp.md)   
 [tmpfile_s](../../c-runtime-library/reference/tmpfile-s.md)