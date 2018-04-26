---
title: strncmp、wcsncmp、_mbsncmp、_mbsncmp_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- strncmp
- _mbsncmp
- wcsncmp
- _mbsncmp_l
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _ftcsnccmp
- _ftcsncmp
- _tcsncmp
- _tcsnccmp
- strncmp
- _mbsncmp
- wcsncmp
dev_langs:
- C++
helpviewer_keywords:
- _tcsnccmp function
- ftcsncmp function
- wcsncmp function
- _ftcsncmp function
- _mbsncmp function
- tcsncmp function
- mbsncmp function
- _mbsncmp_l function
- mbsncmp_l function
- strncmp function
- strings [C++], comparing characters of
- string comparison [C++], strncmp function
- _tcsncmp function
- tcsnccmp function
- ftcsnccmp function
- characters [C++], comparing
- _ftcsnccmp function
ms.assetid: 2fdbf4e6-77da-4b59-9086-488f6066b8af
caps.latest.revision: 28
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 924c3c2bd6517d5a8a8996a6e5983ed7d143dbcf
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="strncmp-wcsncmp-mbsncmp-mbsncmpl"></a>strncmp、wcsncmp、_mbsncmp、_mbsncmp_l

比較最多兩個字串的指定字元計數。

> [!IMPORTANT]
> **_mbsncmp**和 **_mbsncmp_l**不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
int strncmp(
   const char *string1,
   const char *string2,
   size_t count
);
int wcsncmp(
   const wchar_t *string1,
   const wchar_t *string2,
   size_t count
);
int _mbsncmp(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
int _mbsncmp_l(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count,
   _locale_t locale
);int _mbsnbcmp(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
```

### <a name="parameters"></a>參數

*string1*， *string2*<br/>
要比較的字串。

*count*<br/>
要比較的字元數。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

傳回值會指出子字串的關聯性*string1*和*string2* ，如下所示。

|傳回值|描述|
|------------------|-----------------|
|< 0|*string1*子字串小於*string2*子字串|
|0|*string1*子字串等於*string2*子字串|
|> 0|*string1*子字串大於*string2*子字串|

參數驗證錯誤時， **_mbsncmp**和 **_mbsncmp_l**傳回 **_NLSCMPERROR**，定義在\<h > 和\<m >。

## <a name="remarks"></a>備註

**Strncmp**函式會執行序數比較的第一個最*計數*字串中字元*string1*和*string2*和傳回值，指出子字串之間的關聯性。 **strncmp**是區分大小寫版本的 **_strnicmp**。 **wcsncmp**和 **_mbsncmp**是區分大小寫版本的 **_wcsnicmp**和 **_mbsnicmp**。

**wcsncmp**和 **_mbsncmp**是寬字元和多位元組字元版本的**strncmp**。 引數**wcsncmp**是寬字元字串; **_mbsncmp**是多位元組字元字串。 **_mbsncmp**根據多位元組字碼頁辨識多位元組字元序列，並傳回 **_NLSCMPERROR**在發生錯誤。

此外， **_mbsncmp**和 **_mbsncmp_l**驗證的參數。 如果*string1*或*string2*為 null 指標，無效參數處理常式會叫用中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 若要繼續，允許執行 **_mbsncmp**和 **_mbsncmp_l**傳回 **_NLSCMPERROR**並設定**errno**至**EINVAL**。 **strncmp**和**wcsncmp**不會驗證它們的參數。 除此之外，這些函式的行為相同。

比較行為 **_mbsncmp**和 **_mbsncmp_l**的設定會受到**LC_CTYPE**之地區設定分類設定。 這會控制對多位元組字元的開頭和結尾位元組的偵測。 如需詳細資訊，請參閱 [setlocale](setlocale-wsetlocale.md)。 **_Mbsncmp**函式會針對地區設定相關行為使用目前的地區設定。 **_Mbsncmp_l**函式是完全相同，不同之處在於它會使用*地區設定*參數改為。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。 如果地區設定是單一位元組地區設定，這些函式的行為等同於**strncmp**。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsnccmp**|**strncmp**|**_mbsncmp**|**wcsncmp**|
|**_tcsncmp**|**strncmp**|**_mbsnbcmp**|**wcsncmp**|
|**_tccmp**|巨集或內嵌函式的對應|**_mbsncmp**|巨集或內嵌函式的對應|
|**不適用**|**不適用**|**_mbsncmp_l**|**不適用**|

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**strncmp**|\<string.h>|
|**wcsncmp**|\<string.h> 或 \<wchar.h>|
|**_mbsncmp**， **_mbsncmp_l**|\<mbstring.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_strncmp.c
#include <string.h>
#include <stdio.h>

char string1[] = "The quick brown dog jumps over the lazy fox";
char string2[] = "The QUICK brown fox jumps over the lazy dog";

int main( void )
{
   char tmp[20];
   int result;
   printf( "Compare strings:\n      %s\n      %s\n\n",
           string1, string2 );
   printf( "Function:   strncmp (first 10 characters only)\n" );
   result = strncmp( string1, string2 , 10 );
   if( result > 0 )
      strcpy_s( tmp, sizeof(tmp), "greater than" );
   else if( result < 0 )
      strcpy_s( tmp, sizeof(tmp), "less than" );
   else
      strcpy_s( tmp, sizeof(tmp), "equal to" );
   printf( "Result:      String 1 is %s string 2\n\n", tmp );
   printf( "Function:   strnicmp _strnicmp (first 10 characters only)\n" );
   result = _strnicmp( string1, string2, 10 );
   if( result > 0 )
      strcpy_s( tmp, sizeof(tmp), "greater than" );
   else if( result < 0 )
      strcpy_s( tmp, sizeof(tmp), "less than" );
   else
      strcpy_s( tmp, sizeof(tmp), "equal to" );
   printf( "Result:      String 1 is %s string 2\n", tmp );
}
```

```Output
Compare strings:
      The quick brown dog jumps over the lazy fox
      The QUICK brown fox jumps over the lazy dog

Function:   strncmp (first 10 characters only)
Result:      String 1 is greater than string 2

Function:   strnicmp _strnicmp (first 10 characters only)
Result:      String 1 is equal to string 2
```

## <a name="see-also"></a>另請參閱

[字串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbsnbcmp、_mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_mbsnbicmp、_mbsnbicmp_l](mbsnbicmp-mbsnbicmp-l.md)<br/>
[strcmp、wcscmp、_mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strcoll 函式](../../c-runtime-library/strcoll-functions.md)<br/>
[_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr、wcsrchr、_mbsrchr、_mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset、_strset_l、_wcsset、_wcsset_l、_mbsset、_mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn、wcsspn、_mbsspn、_mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
