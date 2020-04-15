---
title: _itoa,_itow功能
ms.date: 4/2/2020
api_name:
- itoa
- _itoa
- ltoa
- _ltoa
- ultoa
- _ultoa
- _i64toa
- _ui64toa
- _itow
- _ltow
- _ultow
- _i64tow
- _ui64tow
- _o__i64toa
- _o__i64tow
- _o__itoa
- _o__itow
- _o__ltoa
- _o__ltow
- _o__ui64toa
- _o__ui64tow
- _o__ultoa
- _o__ultow
api_location:
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
- api-ms-win-crt-convert-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _itoa
- _ltoa
- _ultoa
- _i64toa
- _ui64toa
- _itow
- _ltow
- _ultow
- _i64tow
- _ui64tow
- itoa
- ltoa
- ultoa
- i64toa
- ui64toa
- itow
- ltow
- ultow
- i64tow
- ui64tow
- itot
- _itot
- ltot
- _ltot
- ultot
- _ultot
- i64tot
- _i64tot
- ui64tot
- _ui64tot
- _MAX_ITOSTR_BASE16_COUNT
- _MAX_ITOSTR_BASE10_COUNT
- _MAX_ITOSTR_BASE8_COUNT
- _MAX_ITOSTR_BASE2_COUNT
- _MAX_LTOSTR_BASE16_COUNT
- _MAX_LTOSTR_BASE10_COUNT
- _MAX_LTOSTR_BASE8_COUNT
- _MAX_LTOSTR_BASE2_COUNT
- _MAX_ULTOSTR_BASE16_COUNT
- _MAX_ULTOSTR_BASE10_COUNT
- _MAX_ULTOSTR_BASE8_COUNT
- _MAX_ULTOSTR_BASE2_COUNT
- _MAX_I64TOSTR_BASE16_COUNT
- _MAX_I64TOSTR_BASE10_COUNT
- _MAX_I64TOSTR_BASE8_COUNT
- _MAX_I64TOSTR_BASE2_COUNT
- _MAX_U64TOSTR_BASE16_COUNT
- _MAX_U64TOSTR_BASE10_COUNT
- _MAX_U64TOSTR_BASE8_COUNT
- _MAX_U64TOSTR_BASE2_COUNT
helpviewer_keywords:
- _itot function
- ui64toa function
- _ui64toa function
- converting integers
- itot function
- _i64tow function
- _i64toa function
- _itow function
- ui64tow function
- integers, converting
- itoa function
- _ui64tow function
- i64tow function
- itow function
- i64toa function
- converting numbers, to strings
- _itoa function
ms.assetid: 46592a00-77bb-4e73-98c0-bf629d96cea6
ms.openlocfilehash: 0cc084076c5e39843ecc1afa08671ce6b2f06d1d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342707"
---
# <a name="itoa-_itoa-ltoa-_ltoa-ultoa-_ultoa-_i64toa-_ui64toa-_itow-_ltow-_ultow-_i64tow-_ui64tow"></a>itoa、_itoa、ltoa、_ltoa、ultoa、_ultoa、_i64toa、_ui64toa、_itow、_ltow、_ultow、_i64tow、_ui64tow

將整數轉換成字串。 這些函數的更安全的版本可用;請參閱[_itoa_s、_itow_s函數](itoa-s-itow-s.md)。

## <a name="syntax"></a>語法

```C
char * _itoa( int value, char *buffer, int radix );
char * _ltoa( long value, char *buffer, int radix );
char * _ultoa( unsigned long value, char *buffer, int radix );
char * _i64toa( long long value, char *buffer, int radix );
char * _ui64toa( unsigned long long value, char *buffer, int radix );

wchar_t * _itow( int value, wchar_t *buffer, int radix );
wchar_t * _ltow( long value, wchar_t *buffer, int radix );
wchar_t * _ultow( unsigned long value, wchar_t *buffer, int radix );
wchar_t * _i64tow( long long value, wchar_t *buffer, int radix );
wchar_t * _ui64tow( unsigned long long value, wchar_t *buffer, int radix );

// These POSIX versions of the functions have deprecated names:
char * itoa( int value, char *buffer, int radix );
char * ltoa( long value, char *buffer, int radix );
char * ultoa( unsigned long value, char *buffer, int radix );

// The following template functions are C++ only:
template <size_t size>
char *_itoa( int value, char (&buffer)[size], int radix );

template <size_t size>
char *_itoa( long value, char (&buffer)[size], int radix );

template <size_t size>
char *_itoa( unsigned long value, char (&buffer)[size], int radix );

template <size_t size>
char *_i64toa( long long value, char (&buffer)[size], int radix );

template <size_t size>
char * _ui64toa( unsigned long long value, char (&buffer)[size], int radix );

template <size_t size>
wchar_t * _itow( int value, wchar_t (&buffer)[size], int radix );

template <size_t size>
wchar_t * _ltow( long value, wchar_t (&buffer)[size], int radix );

template <size_t size>
wchar_t * _ultow( unsigned long value, wchar_t (&buffer)[size], int radix );

template <size_t size>
wchar_t * _i64tow( long long value, wchar_t (&buffer)[size], int radix );

template <size_t size>
wchar_t * _ui64tow( unsigned long long value, wchar_t (&buffer)[size],
   int radix );
```

### <a name="parameters"></a>參數

*值*<br/>
要轉換的數字。

*緩衝區*<br/>
保存轉換結果的緩衝區。

*拉迪克斯*<br/>
用於轉換*值*的基數,必須在 2-36 範圍內。

*大小*<br/>
緩衝區的長度(以字元類型的單位為單位)。 此參數從C++中的*緩衝區*參數推斷。

## <a name="return-value"></a>傳回值

每個函數都傳回一個指向*緩衝區的指標*。 不會傳回錯誤。

## <a name="remarks"></a>備註

** **_itoa、_ltoa、_ultoa、_i64toa **_i64toa**和 **_ui64toa**函數將給定*值*參數的數位轉換為 null 端 **_ltoa**接字串,並將結果 **(_itoa、_ltoa**和 **_ultoa****_ltoa**最多 33 個字元)和緩衝區*中***65 個字元_i64toa**和 **_ultoa****_ui64toa)。** 如果*半徑*等於 10,*並且值*為負數,則存儲字串的第一個字元是負**-** 號 ()。 ** **_itow、_ltow、_ultow、_i64tow **_i64tow**和 **_ui64tow****_ltow****_ultow****_itoa**函數分別為 **_itoa、_ltoa、_ultoa、_i64toa**和 **_i64toa****_ui64toa**的寬 **_ultoa**字元版本 。

> [!IMPORTANT]
> 這些函數可以寫入緩衝區的末尾太小。 為了防止緩衝區溢出,請確保*緩衝區*足夠大,可以容納轉換的數位加上尾隨的空字元和符號字元。 濫用這些功能可能會導致代碼出現嚴重的安全問題。

由於其潛在的安全問題,默認情況下,這些函數會導致棄用警告[C4996:](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)**此函數或變數可能不安全。請考慮改用***safe_function。* **要禁用棄用,請使用_CRT_SECURE_NO_WARNINGS。** 我們建議您更改原始碼以使用警告訊息建議的*safe_function。* 更安全的函數不會寫入比指定的緩衝區大小更多的字元。 有關詳細資訊,請參閱[_itoa_s,_itow_s函數](itoa-s-itow-s.md)。

要在不使用棄用警告的情況下使用這些函數,請先定義 **_CRT_SECURE_NO_WARNINGS**預處理器宏,然後再包括任何 CRT 標頭。 通過將 **/D_CRT_SECURE_NO_WARNINGS**編譯器選項添加到**cl**命令,可以在開發人員命令提示符中的命令列上執行此操作。 否則,在源檔中定義宏。 如果使用預編譯標頭,請在預編譯標頭頂部定義宏,包括檔*pch.h(Visual* Studio 2017 和更早版本中的*stdafx.h)。* 要在原始碼中定義巨集,請在包含任何 CRT 標頭之前使用 **#define**指令,如以下範例所示:

```C
By default, this function's global state is scoped to the application. To change this, see [Global state in the CRT](../global-state.md).

#define _CRT_SECURE_NO_WARNINGS 1
#include <stdlib.h>
```

在C++,這些函數具有範本重載,用於調用其更安全的對應函數。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。

POSIX 名稱**itoa、ltoa**和**ultoa** ** ****_ltoa**作為 **_itoa、_ltoa**和 **_ultoa**函數的別名存在。 POSIX 名稱被棄用,因為它們不遵循 ISO C 特定於實現的全域函數名稱約定。預設情況下,這些函數會導致棄用警告[C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md):**此專案的 POSIX 名稱被棄用。相反,請使用 ISO C 和C++符合性名稱:new_name** * *。 我們建議您更改原始程式碼以使用這些函數的更安全版本 **,_itoa_s、_ltoa_s**或 **_ultoa_s。** **_ltoa_s** 有關詳細資訊,請參閱[_itoa_s,_itow_s函數](itoa-s-itow-s.md)。

對於原始碼可移植性,您可能更喜歡在代碼中保留 POSIX 名稱。 要在不使用棄用警告的情況下使用這些函數,請先定義 **_CRT_NONSTDC_NO_WARNINGS**和 **_CRT_SECURE_NO_WARNINGS**預處理器宏,然後再包括任何 CRT 標頭。 通過將 **/D_CRT_SECURE_NO_WARNINGS**和 **/D_CRT_NONSTDC_NO_WARNINGS**編譯器選項添加到**cl**命令,可以在開發人員命令提示符中的命令列上執行此操作。 否則,請定義源檔中的宏。 如果使用預編譯標頭,請定義預編譯標頭頂部的宏包括檔。 要在原始碼中定義巨集,請在包含任何 CRT 標頭之前使用 **#define**指令,如以下範例所示:

```C
#define _CRT_NONSTDC_NO_WARNINGS 1
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdlib.h>
```

### <a name="maximum-conversion-count-macros"></a>最大轉化計數宏

為了説明您為轉換創建安全緩衝區,CRT 包含一些方便的宏。 這些定義轉換多個常見基的每個整數類型(包括空終止符和符號字元)的最長可能值所需的緩衝區大小。 為了確保轉換緩衝區足夠大,足以接收*radix*指定的基中的任何轉換,在分配緩衝區時使用這些定義的宏之一。 這有助於防止將積分類型轉換為字串時緩衝區溢出錯誤。 當您在源中包括 stdlib.h 或 wchar.h 時,將定義這些宏。

要在字串轉換函數中使用這些宏之一,請聲明相應字元類型的轉換緩衝區,並將整數類型和基的宏值用作緩衝區維度。 下表列出一個適用於列出的基礎的每個函數的巨集:

||||
|-|-|-|
|函式|radix|巨集|
|**_itoa**, **_itow**|16<br/>10<br/>8<br/>2|**_MAX_ITOSTR_BASE16_COUNT**<br/>**_MAX_ITOSTR_BASE10_COUNT**<br/>**_MAX_ITOSTR_BASE8_COUNT**<br/>**_MAX_ITOSTR_BASE2_COUNT**|
|**_ltoa**, **_ltow**|16<br/>10<br/>8<br/>2|**_MAX_LTOSTR_BASE16_COUNT**<br/>**_MAX_LTOSTR_BASE10_COUNT**<br/>**_MAX_LTOSTR_BASE8_COUNT**<br/>**_MAX_LTOSTR_BASE2_COUNT**|
|**_ultoa**, **_ultow**|16<br/>10<br/>8<br/>2|**_MAX_ULTOSTR_BASE16_COUNT**<br/>**_MAX_ULTOSTR_BASE10_COUNT**<br/>**_MAX_ULTOSTR_BASE8_COUNT**<br/>**_MAX_ULTOSTR_BASE2_COUNT**|
|**_i64toa**, **_i64tow**|16<br/>10<br/>8<br/>2|**_MAX_I64TOSTR_BASE16_COUNT**<br/>**_MAX_I64TOSTR_BASE10_COUNT**<br/>**_MAX_I64TOSTR_BASE8_COUNT**<br/>**_MAX_I64TOSTR_BASE2_COUNT**|
|**_ui64toa**, **_ui64tow**|16<br/>10<br/>8<br/>2|**_MAX_U64TOSTR_BASE16_COUNT**<br/>**_MAX_U64TOSTR_BASE10_COUNT**<br/>**_MAX_U64TOSTR_BASE8_COUNT**<br/>**_MAX_U64TOSTR_BASE2_COUNT**|

此範例使用轉換計數巨集定義足夠大的緩衝區,以包含基 2 中**長的未簽名長**緩衝區:

```cpp
#include <wchar.h>
#include <iostream>
int main()
{
    wchar_t buffer[_MAX_U64TOSTR_BASE2_COUNT];
    std:wcout << _ui64tow(0xFFFFFFFFFFFFFFFFull, buffer, 2) << std::endl;
}
```

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_itot**|**_itoa**|**_itoa**|**_itow**|
|**_ltot**|**_ltoa**|**_ltoa**|**_ltow**|
|**_ultot**|**_ultoa**|**_ultoa**|**_ultow**|
|**_i64tot**|**_i64toa**|**_i64toa**|**_i64tow**|
|**_ui64tot**|**_ui64toa**|**_ui64toa**|**_ui64tow**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**伊托亞**,**伊托亞**,**烏爾托亞**|\<stdlib.h>|
|**_itoa**, **_ltoa**, **_ultoa**, **_i64toa**, **_ui64toa**|\<stdlib.h>|
|**_itow,** **_ltow**, **_ultow**, **_i64tow**, **_ui64tow**|\<stdlib.h> 或 \<wchar.h>|

這些函數和宏特定於Microsoft。 如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

此示例演示了某些整數轉換函數的使用。 請注意使用 **_CRT_SECURE_NO_WARNINGS**宏來靜默警告 C4996。

```C
// crt_itoa.c
// Compile by using: cl /W4 crt_itoa.c
// This program makes use of the _itoa functions
// in various examples.

#define _CRT_SECURE_NO_WARNINGS 1
#include <stdio.h>      // for printf
#include <string.h>     // for strnlen
#include <stdlib.h>     // for _countof, _itoa fns, _MAX_COUNT macros

int main(void)
{
    char buffer[_MAX_U64TOSTR_BASE2_COUNT];
    int r;

    for (r = 10; r >= 2; --r)
    {
        _itoa(-1, buffer, r);
        printf("base %d: %s (%d chars)\n", r, buffer,
            strnlen(buffer, _countof(buffer)));
    }
    printf("\n");

    for (r = 10; r >= 2; --r)
    {
        _i64toa(-1LL, buffer, r);
        printf("base %d: %s (%d chars)\n", r, buffer,
            strnlen(buffer, _countof(buffer)));
    }
    printf("\n");

    for (r = 10; r >= 2; --r)
    {
        _ui64toa(0xffffffffffffffffULL, buffer, r);
        printf("base %d: %s (%d chars)\n", r, buffer,
            strnlen(buffer, _countof(buffer)));
    }
}
```

```Output
base 10: -1 (2 chars)
base 9: 12068657453 (11 chars)
base 8: 37777777777 (11 chars)
base 7: 211301422353 (12 chars)
base 6: 1550104015503 (13 chars)
base 5: 32244002423140 (14 chars)
base 4: 3333333333333333 (16 chars)
base 3: 102002022201221111210 (21 chars)
base 2: 11111111111111111111111111111111 (32 chars)

base 10: -1 (2 chars)
base 9: 145808576354216723756 (21 chars)
base 8: 1777777777777777777777 (22 chars)
base 7: 45012021522523134134601 (23 chars)
base 6: 3520522010102100444244423 (25 chars)
base 5: 2214220303114400424121122430 (28 chars)
base 4: 33333333333333333333333333333333 (32 chars)
base 3: 11112220022122120101211020120210210211220 (41 chars)
base 2: 1111111111111111111111111111111111111111111111111111111111111111 (64 chars)

base 10: 18446744073709551615 (20 chars)
base 9: 145808576354216723756 (21 chars)
base 8: 1777777777777777777777 (22 chars)
base 7: 45012021522523134134601 (23 chars)
base 6: 3520522010102100444244423 (25 chars)
base 5: 2214220303114400424121122430 (28 chars)
base 4: 33333333333333333333333333333333 (32 chars)
base 3: 11112220022122120101211020120210210211220 (41 chars)
base 2: 1111111111111111111111111111111111111111111111111111111111111111 (64 chars)
```

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[_itoa_s,_itow_s功能](itoa-s-itow-s.md)<br/>
