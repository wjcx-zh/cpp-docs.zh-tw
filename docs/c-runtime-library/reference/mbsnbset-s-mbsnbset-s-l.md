---
title: _mbsnbset_s、_mbsnbset_s_l
ms.date: 11/04/2016
apiname:
- _mbsnbset_s_l
- _mbsnbset_s
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
apitype: DLLExport
f1_keywords:
- mbsnbset_s
- _mbsnbset_s_l
- _mbsnbset_s
- mbsnbset_s_l
helpviewer_keywords:
- tcsnset_s function
- mbsnbset_s function
- mbsnbset_s_l function
- _mbsnbset_s_l function
- _tcsnset_s_l function
- _mbsnbset_s function
- _tcsnset_s function
- tcsnset_s_l function
ms.assetid: 811f92c9-cc31-4bbd-8017-2d1bfc6fb96f
ms.openlocfilehash: 5d021f147ba407f5b0b7316afc7cfd79fe300997
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50580969"
---
# <a name="mbsnbsets-mbsnbsetsl"></a>_mbsnbset_s、_mbsnbset_s_l

設定第一個**n**個位元組的多位元組字元字串，為指定的字元。 這些是 [_mbsnbset、_mbsnbset_l](mbsnbset-mbsnbset-l.md) 的版本，具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。

> [!IMPORTANT]
> 這個應用程式開發介面不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
errno_t _mbsnbset_s(
   unsigned char *str,
   size_t size,
   unsigned int c,
   size_t count
);
errno_t _mbsnbset_s_l(
   unsigned char *str,
   size_t size,
   unsigned int c,
   size_t count,
   _locale_t locale
);
template <size_t size>
errno_t _mbsnbset_s(
   unsigned char (&str)[size],
   unsigned int c,
   size_t count
); // C++ only
template <size_t size>
errno_t _mbsnbset_s_l(
   unsigned char (&str)[size],
   unsigned int c,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>參數

*str*<br/>
待變更字串。

*size*<br/>
字串緩衝區的大小。

*C*<br/>
單一位元組或多位元組字元的設定。

*count*<br/>
要設定的位元組數目。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

如果成功則為零，否則為錯誤碼。

## <a name="remarks"></a>備註

**_Mbsnbset_s**並 **_mbsnbset_s_l**函式會將，最多會第一個*計數*位元組*str*到*c*. 如果*計數*大於的長度*str*，長度*str*改用*計數*。 如果*c*是多位元組字元，而且不能完全讀入指定的最後一個位元組的方式來設定*計數*，最後一個位元組會以空白的字元填補。 **_mbsnbset_s**並 **_mbsnbset_s_l**未放置的終止 null 結尾*str*。

**_mbsnbset_s**並 **_mbsnbset_s_l**類似 **_mbsnset**，只不過它們設定*計數*位元組而非*計數*字元*c*。

如果*str*是**NULL**或*計數*是零，此函式會產生無效參數例外狀況，如中所述[Parameter Validation](../../c-runtime-library/parameter-validation.md). 如果允許繼續，請執行**errno**設為**EINVAL**和函式會傳回**NULL**。 此外，如果*c*不是有效的多位元組字元， **errno**設定為**EINVAL**並改用一個空格。

輸出值的設定會影響**LC_CTYPE**地區設定分類設定; 請參閱[setlocale、 _wsetlocale](setlocale-wsetlocale.md)如需詳細資訊。 **_Mbsnbset_s**此函式版本會針對地區設定相關行為; 使用目前的地區設定 **_mbsnbset_s_l**版本也一樣，不同之處在於它會改為使用地區設定參數的傳入。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

在 C++ 中，樣板多載簡化了這些函式的使用方式；此多載可自動推斷緩衝區長度，因此不須指定大小引數。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

這些函式的偵錯版本會先用 0xFD 填入緩衝區。 若要停用此行為，請使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnset_s**|**_strnset_s**|**_mbsnbset_s**|**_wcsnset_s**|
|**_tcsnset_s_l**|`_strnset_s _l`|**_mbsnbset_s_l**|**_wcsnset_s_l**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_mbsnbset_s**|\<mbstring.h>|
|**_mbsnbset_s_l**|\<mbstring.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_mbsnbset_s.c
#include <mbstring.h>
#include <stdio.h>

int main( void )
{
   char string[15] = "This is a test";
   /* Set not more than 4 bytes of string to be *'s */
   printf( "Before: %s\n", string );
   _mbsnbset_s( string, sizeof(string), '*', 4 );
   printf( "After:  %s\n", string );
}
```

## <a name="output"></a>輸出

```Output
Before: This is a test
After:  **** is a test
```

## <a name="see-also"></a>另請參閱

[字串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat、_mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_strnset、_strnset_l、_wcsnset、_wcsnset_l、_mbsnset、_mbsnset_l](strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md)<br/>
[_strset、_strset_l、_wcsset、_wcsset_l、_mbsset、_mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
