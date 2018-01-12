---
title: "strncat_s、_strncat_s_l、wcsncat_s、_wcsncat_s_l、_mbsncat_s、_mbsncat_s_l | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wcsncat_s_l
- wcsncat_s
- _mbsncat_s_l
- _mbsncat_s
- strncat_s
- _strncat_s_l
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
- strncat_s_l
- _mbsncat_s_l
- _tcsncat_s
- wcsncat_s
- wcsncat_s_l
- strncat_s
- _mbsncat_s
- _tcsncat_s_l
dev_langs: C++
helpviewer_keywords:
- concatenating strings
- _mbsncat_s function
- mbsncat_s_l function
- _tcsncat_s function
- _mbsncat_s_l function
- strncat_s function
- strings [C++], appending
- strncat_s_l function
- string concatenation [C++]
- _tcsncat_s_l function
- wcsncat_s function
- appending strings
- wcsncat_s_l function
- mbsncat_s function
ms.assetid: de77eca2-4d9c-4e66-abf2-a95fefc21e5a
caps.latest.revision: "42"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 789ac892ab4d91ea88e563079599ae4422e55a79
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="strncats-strncatsl-wcsncats-wcsncatsl-mbsncats-mbsncatsl"></a>strncat_s、_strncat_s_l、wcsncat_s、_wcsncat_s_l、_mbsncat_s、_mbsncat_s_l
將字元附加至字串。 這些版本的 [strncat、_strncat_l、wcsncat、_wcsncat_l、_mbsncat、_mbsncat_l](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md) 具有 [CRT 的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。  
  
> [!IMPORTANT]
>  在 Windows 執行階段中執行的應用程式中無法使用 `_mbsncat_s` 和 `_mbsncat_s_l`。 如需詳細資訊，請參閱 [/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>語法  
  
```  
errno_t strncat_s(  
   char *strDest,  
   size_t numberOfElements,  
   const char *strSource,  
   size_t count  
);  
errno_t _strncat_s_l(  
   char *strDest,  
   size_t numberOfElements,  
   const char *strSource,  
   size_t count,  
   _locale_t locale  
);  
errno_t wcsncat_s(  
   wchar_t *strDest,  
   size_t numberOfElements,  
   const wchar_t *strSource,  
   size_t count   
);  
errno_t _wcsncat_s_l(  
   wchar_t *strDest,  
   size_t numberOfElements,  
   const wchar_t *strSource,  
   size_t count,  
   _locale_t locale  
);  
errno_t _mbsncat_s(  
   unsigned char *strDest,  
   size_t numberOfElements,  
   const unsigned char *strSource,  
   size_t count  
);  
errno_t _mbsncat_s_l(  
   unsigned char *strDest,  
   size_t numberOfElements,  
   const unsigned char *strSource,  
   size_t count,  
   _locale_t locale  
);  
template <size_t size>  
errno_t strncat_s(  
   char (&strDest)[size],  
   const char *strSource,  
   size_t count  
); // C++ only  
template <size_t size>  
errno_t _strncat_s_l(  
   char (&strDest)[size],  
   const char *strSource,  
   size_t count,  
   _locale_t locale  
); // C++ only  
template <size_t size>  
errno_t wcsncat_s(  
   wchar_t (&strDest)[size],  
   const wchar_t *strSource,  
   size_t count   
); // C++ only  
template <size_t size>  
errno_t _wcsncat_s_l(  
   wchar_t (&strDest)[size],  
   const wchar_t *strSource,  
   size_t count,  
   _locale_t locale  
); // C++ only  
template <size_t size>  
errno_t _mbsncat_s(  
   unsigned char (&strDest)[size],  
   const unsigned char *strSource,  
   size_t count  
); // C++ only  
template <size_t size>  
errno_t _mbsncat_s_l(  
   unsigned char (&strDest)[size],  
   const unsigned char *strSource,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### <a name="parameters"></a>參數  
 [輸出] `strDest`  
 以 Null 終止的目的字串。  
  
 [in]`numberOfElements`  
 目的緩衝區大小。  
  
 [in]`strSource`  
 以 Null 結束的來源字串。  
  
 [in]`count`  
 要附加的字元數或 [_TRUNCATE](../../c-runtime-library/truncate.md)。  
  
 [輸入] `locale`  
 要使用的地區設定。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 0，如果失敗，則為錯誤碼。  
  
### <a name="error-conditions"></a>錯誤狀況  
  
|`strDestination`|`numberOfElements`|`strSource`|傳回值|`strDestination` 的內容。|  
|----------------------|------------------------|-----------------|------------------|----------------------------------|  
|`NULL` 或未終止的|any|any|`EINVAL`|未修改|  
|any|any|`NULL`|`EINVAL`|未修改|  
|any|0 或太小|any|`ERANGE`|未修改|  
  
## <a name="remarks"></a>備註  
 這些函式嘗試將 `strSource` 的前 `D` 個字元附加到 `strDest` 結尾，其中 `D` 是較小的 `count` 且長度為 `strSource`。 如果尾部附加這些 `D` 字元適合 `strDest` (其大小指定為 `numberOfElements`)，並仍留出空間給以 Null 終止的字元，則附加這些字元，從 `strDest` 的原始終止 Null 開始，再附加新的終止 Null；否則 `strDest`[0] 會設成 Null 字元並叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  
  
 上述段落有一個例外狀況。 如果 `count` 是 [_TRUNCATE](../../c-runtime-library/truncate.md)，則 `strSource` 會盡量多地調整附加至 `strDest`，同時保留附加終止 Null 的空間。  
  
 例如，套用至物件的  
  
 `char dst[5];`  
  
 `strncpy_s(dst, _countof(dst), "12", 2);`  
  
 `strncat_s(dst, _countof(dst), "34567", 3);`  
  
 表示我們要求 `strncat_s` 將三個字元附加至緩衝區中五個字元長的兩個字元後，這不會留下任何空間給以 Null 終止的字元，因此 `strncat_s` 會歸零字串，並呼叫無效的參數處理常式。  
  
 如果需要截斷行為，請使用 `_TRUNCATE` 或據以調整 `size` 參數︰  
  
 `strncat_s(dst, _countof(dst), "34567", _TRUNCATE);`  
  
 或  
  
 `strncat_s(dst, _countof(dst), "34567", _countof(dst)-strlen(dst)-1);`  
  
 在所有案例中，產生的字串都終止於 Null 字元。 如果在重疊的字串之間執行複製，則行為是未定義的。  
  
 如果 `strSource` 或 `strDest` 為 `NULL`，或 `numberOfElements` 為零，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，函式會傳回 `EINVAL` 但不修改其參數。  
  
 `wcsncat_s` 和 `_mbsncat_s` 是寬字元和多位元組字元版本的 `strncat_s`。 `wcsncat_s` 的字串引數與傳回值是寬字元字串；`_mbsncat_s` 的引數和傳回值則是多位元組字元字串。 除此之外，這三個函式的行為相同。  
  
 輸出值會受到地區設定的 `LC_CTYPE` 分類設定影響；如需詳細資訊，請參閱 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。 這些沒有 `_l` 後置字元的函式版本，會針對此與地區設定相關的行為使用目前的地區設定；具有 `_l` 後置字元的版本也一樣，只不過它們會改用傳遞的地區設定參數。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。  
  
 C++ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 (因而不須指定大小引數)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。  
  
 這些函式的偵錯版本會先用 0xFD 填入緩衝區。 若要停用此行為，請使用 [_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md)。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcsncat_s`|`strncat_s`|`_mbsnbcat_s`|`wcsncat_s`|  
|`_tcsncat_s_l`|`_strncat_s_l`|`_mbsnbcat_s_l`|`_wcsncat_s_l`|  
  
 `_strncat_s_l` 和 `_wcsncat_s_l` 沒有任何地區設定相依性，僅供 `_tcsncat_s_l` 所用。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`strncat_s`|\<string.h>|  
|`wcsncat_s`|\<string.h> 或 \<wchar.h>|  
|`_mbsncat_s`, `_mbsncat_s_l`|\<mbstring.h>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_strncat_s.cpp  
// compile with: /MTd  
  
// These #defines enable secure template overloads  
// (see last part of Examples() below)  
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES 1   
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT 1  
  
#include <stdio.h>  
#include <stdlib.h>  
#include <string.h>  
#include <crtdbg.h>  // For _CrtSetReportMode  
#include <errno.h>  
  
// This example uses a 10-byte destination buffer.  
  
errno_t strncat_s_tester( const char * initialDest,  
                          const char * src,  
                          int count )  
{  
   char dest[10];  
   strcpy_s( dest, _countof(dest), initialDest );  
  
   printf_s( "\n" );  
  
   if ( count == _TRUNCATE )  
      printf_s( "Appending '%s' to %d-byte buffer dest with truncation semantics\n",  
               src, _countof(dest) );  
   else  
      printf_s( "Appending %d chars of '%s' to %d-byte buffer dest\n",  
              count, src, _countof(dest) );  
  
   printf_s( "    old contents of dest: '%s'\n", dest );  
  
   errno_t err = strncat_s( dest, _countof(dest), src, count );  
  
   printf_s( "    new contents of dest: '%s'\n", dest );  
  
   return err;  
}  
  
void Examples()  
{  
   strncat_s_tester( "hi ", "there", 4 );  
   strncat_s_tester( "hi ", "there", 5 );  
   strncat_s_tester( "hi ", "there", 6 );  
  
   printf_s( "\nDestination buffer too small:\n" );  
   strncat_s_tester( "hello ", "there", 4 );  
  
   printf_s( "\nTruncation examples:\n" );  
  
   errno_t err = strncat_s_tester( "hello ", "there", _TRUNCATE );  
   printf_s( "    truncation %s occur\n", err == STRUNCATE ? "did"  
                                                       : "did not" );  
  
   err = strncat_s_tester( "hello ", "!", _TRUNCATE );  
   printf_s( "    truncation %s occur\n", err == STRUNCATE ? "did"  
                                                       : "did not" );  
  
   printf_s( "\nSecure template overload example:\n" );  
  
   char dest[10] = "cats and ";  
   strncat( dest, "dachshunds", 15 );  
   // With secure template overloads enabled (see #define  
   // at top of file), the preceding line is replaced by  
   //    strncat_s( dest, _countof(dest), "dachshunds", 15 );  
   // Instead of causing a buffer overrun, strncat_s invokes  
   // the invalid parameter handler.  
   // If secure template overloads were disabled, strncat would  
   // append "dachshunds" and overrun the dest buffer.  
   printf_s( "    new contents of dest: '%s'\n", dest );  
}  
  
void myInvalidParameterHandler(  
   const wchar_t* expression,  
   const wchar_t* function,   
   const wchar_t* file,   
   unsigned int line,   
   uintptr_t pReserved)  
{  
   wprintf_s(L"Invalid parameter handler invoked: %s\n", expression);  
}  
  
int main( void )  
{  
   _invalid_parameter_handler oldHandler, newHandler;  
  
   newHandler = myInvalidParameterHandler;  
   oldHandler = _set_invalid_parameter_handler(newHandler);  
   // Disable the message box for assertions.  
   _CrtSetReportMode(_CRT_ASSERT, 0);  
  
   Examples();  
}  
```  
  
```Output  
Appending 4 chars of 'there' to 10-byte buffer dest  
    old contents of dest: 'hi '  
    new contents of dest: 'hi ther'  
  
Appending 5 chars of 'there' to 10-byte buffer dest  
    old contents of dest: 'hi '  
    new contents of dest: 'hi there'  
  
Appending 6 chars of 'there' to 10-byte buffer dest  
    old contents of dest: 'hi '  
    new contents of dest: 'hi there'  
  
Destination buffer too small:  
  
Appending 4 chars of 'there' to 10-byte buffer dest  
    old contents of dest: 'hello '  
Invalid parameter handler invoked: (L"Buffer is too small" && 0)  
    new contents of dest: ''  
  
Truncation examples:  
  
Appending 'there' to 10-byte buffer dest with truncation semantics  
    old contents of dest: 'hello '  
    new contents of dest: 'hello the'  
    truncation did occur  
  
Appending '!' to 10-byte buffer dest with truncation semantics  
    old contents of dest: 'hello '  
    new contents of dest: 'hello !'  
    truncation did not occur  
  
Secure template overload example:  
Invalid parameter handler invoked: (L"Buffer is too small" && 0)  
    new contents of dest: ''  
```  
  
## <a name="see-also"></a>請參閱  
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [_mbsnbcat、_mbsnbcat_l](../../c-runtime-library/reference/mbsnbcat-mbsnbcat-l.md)   
 [strcat、wcscat、_mbscat](../../c-runtime-library/reference/strcat-wcscat-mbscat.md)   
 [strcmp、wcscmp、_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strcpy、wcscpy、_mbscpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)   
 [strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [strncpy、_strncpy_l、wcsncpy、_wcsncpy_l、_mbsncpy、_mbsncpy_l](../../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)   
 [_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr、wcsrchr、_mbsrchr、_mbsrchr_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [_strset、_strset_l、_wcsset、_wcsset_l、_mbsset、_mbsset_l](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)   
 [strspn、wcsspn、_mbsspn、_mbsspn_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)