---
title: "strnlen、strnlen_s、wcsnlen、wcsnlen_s、_mbsnlen、_mbsnlen_l、_mbstrnlen、_mbstrnlen_l | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- wcsnlen
- strnlen_s
- _mbstrnlen
- _mbsnlen_l
- _mbstrnlen_l
- strnlen
- wcsnlen_s
- _mbsnlen
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wcsnlen
- strnlen_s
- _mbsnlen
- _mbsnlen_l
- _tcsnlen
- _tcscnlen
- _mbstrnlen_l
- wcsnlen_s
- _mbstrnlen
- strnlen
- _tcscnlen_l
dev_langs: C++
helpviewer_keywords:
- _tcscnlen function
- _mbstrnlen function
- _mbsnlen_l function
- lengths, strings
- mbstrnlen function
- mbsnlen_l function
- _mbstrnlen_l function
- _tcscnlen_l function
- wcsnlen_l function
- _tcsnlen function
- _mbsnlen function
- strnlen function
- mbsnlen function
- wcsnlen_s function
- strnlen_s function
- mbstrnlen_l function
- wcsnlen function
- string length
- strnlen_l function
ms.assetid: cc05ce1c-72ea-4ae4-a7e7-4464e56e5f80
caps.latest.revision: "35"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 59c9d1f893dbc024a0645e70119d1069c3383ed8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="strnlen-strnlens-wcsnlen-wcsnlens-mbsnlen-mbsnlenl-mbstrnlen-mbstrnlenl"></a>strnlen、strnlen_s、wcsnlen、wcsnlen_s、_mbsnlen、_mbsnlen_l、_mbstrnlen、_mbstrnlen_l
使用目前的地區設定或是已傳入的地區設定取得字串的長度。 這些是較安全的 [strlen、wcslen、_mbslen、_mbslen_l、_mbstrlen、_mbstrlen_l](../../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md) 版本。  
  
> [!IMPORTANT]
>  在 Windows 執行階段中執行的應用程式中無法使用 `_mbsnlen`、`_mbsnlen_l`、`_mbstrnlen` 和 `_mbstrnlen_l`。 如需詳細資訊，請參閱 [/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>語法  
  
```  
size_t strnlen(  
   const char *str,  
   size_t numberOfElements   
);  
size_t strnlen_s(  
   const char *str,  
   size_t numberOfElements   
);  
size_t wcsnlen(  
   const wchar_t *str,  
   size_t numberOfElements  
);  
size_t wcsnlen_s(  
   const wchar_t *str,  
   size_t numberOfElements  
);  
size_t _mbsnlen(  
   const unsigned char *str,  
   size_t numberOfElements  
);  
size_t _mbsnlen_l(  
   const unsigned char *str,  
   size_t numberOfElements,  
   _locale_t locale  
);  
size_t _mbstrnlen(  
   const char *str,  
   size_t numberOfElements  
);  
size_t _mbstrnlen_l(  
   const char *str,  
   size_t numberOfElements,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>參數  
 `str`  
 以 Null 結束的字串。  
  
 `numberOfElements`  
 字串緩衝區的大小。  
  
 `locale`  
 要使用的地區設定。  
  
## <a name="return-value"></a>傳回值  
 這些函式會傳回字串中的字元數，但不包含結束的 Null 字元。 若字串的第一個 `numberOfElements` 位元組中沒有 Null 結束字元 (或是 `wcsnlen` 的寬字元)，則會傳回 `numberOfElements` 以指出錯誤情況；以 Null 終止的字串具有絕對小於 `numberOfElements` 的長度。  
  
 若字串包含無效的多位元組字元，`_mbstrnlen` 和 `_mbstrnlen_l` 會傳回 -1。  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  `strnlen` 不是 `strlen` 的取代項目；`strnlen` 僅供用於計算已知大小的緩衝區中，連入的未受信任資料的大小，例如網路封包。 `strnlen` 會計算長度，但如果字串為未結束，就不會經過緩衝區的結尾。 請針對其他情況使用 `strlen`。 (同樣適用於 `wcsnlen`、`_mbsnlen` 和 `_mbstrnlen`)。  
  
 這些函式都會傳回 `str` 中的字元數，但不包含結束的 Null 字元。 但 `strnlen` 和 `strnlen_s` 會將字串解譯為單一位元組字元字串，因此即使字串包含多位元組字元，傳回值也會一律等於位元組數。 `wcsnlen` 和 `wcsnlen_s` 分別是寬字元版本的 `strnlen` 和 `strnlen_s`；`wcsnlen` 和 `wcsnlen_s` 的引數是寬字元，且字元的計數是以寬字元為單位。 除此之外，`wcsnlen` 和 `strnlen` 的行為相同，`strnlen_s` 和 `wcsnlen_s` 也一樣。  
  
 `strnlen``wcsnlen`，和`_mbsnlen`不會驗證它們的參數。 若 `str` 為 `NULL`，會發生存取違規。  
  
 `strnlen_s` 和 `wcsnlen_s` 會驗證其參數。 若 `str` 為 `NULL`，函式會傳回 0。  
  
 `_mbstrnlen` 也會驗證其參數。 如果 `str` 為 `NULL`，或 `numberOfElements` 大於 `INT_MAX`，`_mbstrnlen` 會產生無效的參數例外狀況，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若允許繼續執行，`_mbstrnlen` 會將 `errno` 設為 `EINVAL`，並傳回 -1。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcsnlen`|`strnlen`|`strnlen`|`wcsnlen`|  
|`_tcscnlen`|`strnlen`|`_mbsnlen`|`wcsnlen`|  
|`_tcscnlen_l`|`strnlen`|`_mbsnlen_l`|`wcsnlen`|  
  
 `_mbsnlen` 和 `_mbstrnlen` 會傳回多位元組字元字串中的多位元組字元數。 `_mbsnlen` 會根據目前使用中的多位元組字碼頁，或是根據傳入的地區設定，辨識多位元組字元序列；但不會測試多位元組字元的有效性。 `_mbstrnlen` 會測試多位元組字元的有效性，並辨識多位元組字元的序列。 若傳遞至 `_mbstrnlen` 的字串包含無效的多位元組字元，`errno` 會設為 `EILSEQ`。  
  
 輸出值會受到地區設定的 `LC_CTYPE` 分類設定影響；如需詳細資訊，請參閱 [setlocale、_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。 這些函式的版本均相同，除了沒有 `_l` 後置字元的函式會針對此地區設定的相關行為使用目前的地區設定，而具有 `_l` 後置字元的函式會改用傳入的地區設定參數。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`strnlen`, `strnlen_s`|\<string.h>|  
|`wcsnlen`, `wcsnlen_s`|\<string.h> 或 \<wchar.h>|  
|`_mbsnlen`, `_mbsnlen_l`|\<mbstring.h>|  
|`_mbstrnlen`, `_mbstrnlen_l`|\<stdlib.h>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```C  
// crt_strnlen.c  
  
#include <string.h>  
  
int main()  
{  
   // str1 is 82 characters long. str2 is 159 characters long   
  
   char* str1 = "The length of a string is the number of characters\n"  
               "excluding the terminating null.";  
   char* str2 = "strnlen takes a maximum size. If the string is longer\n"  
                "than the maximum size specified, the maximum size is\n"  
                "returned rather than the actual size of the string.";  
   size_t len;  
   size_t maxsize = 100;  
  
   len = strnlen(str1, maxsize);  
   printf("%s\n Length: %d \n\n", str1, len);  
  
   len = strnlen(str2, maxsize);  
   printf("%s\n Length: %d \n", str2, len);  
}  
```  
  
```Output  
The length of a string is the number of characters  
excluding the terminating null.  
 Length: 82   
  
strnlen takes a maximum size. If the string is longer  
than the maximum size specified, the maximum size is  
returned rather than the actual size of the string.  
 Length: 100   
```  
  
## <a name="see-also"></a>請參閱  
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [setlocale、_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [strncat、_strncat_l、wcsncat、_wcsncat_l、_mbsncat、_mbsncat_l](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)   
 [strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [strcoll 函式](../../c-runtime-library/strcoll-functions.md)   
 [strncpy_s、_strncpy_s_l、wcsncpy_s、_wcsncpy_s_l、_mbsncpy_s、_mbsncpy_s_l](../../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)   
 [strrchr、wcsrchr、_mbsrchr、_mbsrchr_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [_strset、_strset_l、_wcsset、_wcsset_l、_mbsset、_mbsset_l](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)   
 [strspn、wcsspn、_mbsspn、_mbsspn_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)