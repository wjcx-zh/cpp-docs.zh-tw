---
title: _strrev、_wcsrev、_mbsrev、_mbsrev_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _wcsrev
- _mbsrev
- _strrev
- _mbsrev_l
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
- _strrev
- _ftcsrev
- _tcsrev
- mbsrev
- mbsrev_l
- _wcsrev_fstrrev
- _mbsrev
dev_langs:
- C++
helpviewer_keywords:
- _mbsrev_l function
- characters [C++], switching
- _mbsrev function
- strrev function
- _ftcsrev function
- strings [C++], reversing
- wcsrev function
- _strrev function
- mbsrev_l function
- reversing characters in strings
- ftcsrev function
- characters [C++], reversing order
- _wcsrev function
- mbsrev function
- tcsrev function
- _tcsrev function
ms.assetid: 87863e89-4fa0-421c-af48-25d8516fe72f
caps.latest.revision: 25
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f8b925b3c67dda4d29208a7027bb7905502df432
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="strrev-wcsrev-mbsrev-mbsrevl"></a>_strrev、_wcsrev、_mbsrev、_mbsrev_l

反轉字串字元。

> [!IMPORTANT]
> **_mbsrev**和 **_mbsrev_l**不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
char *_strrev(
   char *str
);
wchar_t *_wcsrev(
   wchar_t *str
);
unsigned char *_mbsrev(
   unsigned char *str
);
unsigned char *_mbsrev_l(
   unsigned char *str,
   _locale_t locale
);
```

### <a name="parameters"></a>參數

*str*<br/>
以 Null 終止的待反轉字串。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

傳回變更後字串的指標。 未保留表示錯誤的傳回值。

## <a name="remarks"></a>備註

**_Strrev**函式會反轉順序中的字元*str*。 原地保留終止的 Null 字元。 **_wcsrev**和 **_mbsrev**是寬字元和多位元組字元版本的 **_strrev**。 引數和傳回值 **_wcsrev**是寬字元字串; **_mbsrev**是多位元組字元字串。 如 **_mbsrev**中的每一個多位元組字元的位元組順序*str*則不會變更。 除此之外，這三個函式的行為相同。

**_mbsrev**會驗證其參數。 如果有任一個*string1*或*string2*為 null 指標，無效參數處理常式會叫用中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 若要繼續，允許執行 **_mbsrev**傳回**NULL**並設定**errno**至**EINVAL**。 **_strrev**和 **_wcsrev**不會驗證它們的參數。

輸出值會影響的設定**LC_CTYPE**之地區設定分類設定，請參閱 < [setlocale、 _wsetlocale](setlocale-wsetlocale.md)如需詳細資訊。 這些函式版本是相同的不同之處在於，不是有 **_l**後置詞使用目前的地區設定而沒有 **_l**尾碼改為使用的地區設定參數的傳入。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

> [!IMPORTANT]
> 這些函式可能容易受到緩衝區滿溢的威脅。 緩衝區滿溢可能被當成系統攻擊方式，因為它們可能導致非預期的提高權限。 如需詳細資訊，請參閱 [Avoiding Buffer Overruns (避免緩衝區滿溢)](http://msdn.microsoft.com/library/windows/desktop/ms717795)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsrev**|**_strrev**|**_mbsrev**|**_wcsrev**|
|**n/a**|**n/a**|**_mbsrev_l**|**n/a**|

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_strrev**|\<string.h>|
|**_wcsrev**|\<string.h> 或 \<wchar.h>|
|**_mbsrev**， **_mbsrev_l**|\<mbstring.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_strrev.c
// This program checks a string to see
// whether it is a palindrome: that is, whether
// it reads the same forward and backward.
//

#include <string.h>
#include <stdio.h>

int main( void )
{
   char* string = "Able was I ere I saw Elba";
   int result;

   // Reverse string and compare (ignore case):
   result = _stricmp( string, _strrev( _strdup( string ) ) );
   if( result == 0 )
      printf( "The string \"%s\" is a palindrome\n", string );
   else
      printf( "The string \"%s\" is not a palindrome\n", string );
}
```

```Output
The string "Able was I ere I saw Elba" is a palindrome
```

## <a name="see-also"></a>另請參閱

[字串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcpy、wcscpy、_mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[_strset、_strset_l、_wcsset、_wcsset_l、_mbsset、_mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
