---
title: _itoa，_itow 函式
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 424ee4fb732811bffc6a83c0de57cd35fe747c42
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914658"
---
# <a name="itoa-_itoa-ltoa-_ltoa-ultoa-_ultoa-_i64toa-_ui64toa-_itow-_ltow-_ultow-_i64tow-_ui64tow"></a>itoa、_itoa、ltoa、_ltoa、ultoa、_ultoa、_i64toa、_ui64toa、_itow、_ltow、_ultow、_i64tow、_ui64tow

將整數轉換成字串。 這些函式已有更安全的版本可供使用;請參閱[_itoa_s、_itow_s 函數](itoa-s-itow-s.md)。

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

*基*<br/>
*Value*的轉換所使用的基底，其必須在範圍2-36。

*size*<br/>
緩衝區的長度（以字元類型的單位表示）。 這個參數是從 c + + 中的*buffer*引數推斷而來。

## <a name="return-value"></a>傳回值

所有這些函式都會傳回*緩衝區*的指標。 不會傳回錯誤。

## <a name="remarks"></a>備註

**_Itoa**、 **_ltoa**、 **_ultoa**、 **_i64toa**和 **_ui64toa**函式會將指定*值*引數的數位轉換成以 null 結束的字元字串，並將結果（最多33個字元**用於 _itoa**、 **_ltoa**和 **_ultoa**，而65用於 **_i64toa**和 **_ui64toa**）儲存在*緩衝區*中。 如果*基數*等於10且*值*為負數，則儲存字串的第一個字元是減號（**-**）。 **_Itow**、 **_ltow**、 **_ultow**、 **_i64tow**和 **_ui64tow**函數分別是寬字元版本的 **_itoa**、 **_ltoa**、 **_ultoa**、 **_i64toa**和 **_ui64toa**。

> [!IMPORTANT]
> 這些函式可以寫入超過緩衝區結尾太小的部分。 若要防止緩衝區溢位，請確定*緩衝區*夠大，足以容納轉換的數位加上尾端的 null 字元和正負號字元。 誤用這些函式可能會在您的程式碼中造成嚴重的安全性問題。

基於安全性問題的可能，根據預設，這些函式會造成淘汰警告[C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)：**此函式或變數可能不安全。請考慮改為使用** *safe_function* **。若要停用取代，請使用 _CRT_SECURE_NO_WARNINGS。** 建議您變更原始程式碼，以使用警告訊息所建議的*safe_function* 。 較安全的函式不會寫入比指定緩衝區大小更多的字元。 如需詳細資訊，請參閱[_itoa_s、_itow_s 函數](itoa-s-itow-s.md)。

若要在沒有淘汰警告的情況下使用這些函式，請在包含任何 CRT 標頭之前定義 **_CRT_SECURE_NO_WARNINGS**預處理器宏。 您可以在開發人員命令提示字元中的命令列上執行此動作，方法是將 **/D_CRT_SECURE_NO_WARNINGS**編譯器選項加入**cl**命令。 否則，請在您的原始程式檔中定義宏。 如果您使用先行編譯的標頭，請在先行編譯標頭檔的頂端定義宏，包括 file、 *pch* （Visual Studio 2017 和更早版本中的*stdafx.h* ）。 若要在原始程式碼中定義宏，請在包含任何 CRT 標頭之前使用 **#define**指示詞，如下列範例所示：

```C
By default, this function's global state is scoped to the application. To change this, see [Global state in the CRT](../global-state.md).

#define _CRT_SECURE_NO_WARNINGS 1
#include <stdlib.h>
```

在 c + + 中，這些函式具有可叫用其更安全對應專案的範本多載 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。

POSIX 名稱**itoa**、 **ltoa**和**ultoa**會當做 **_itoa**、 **_ltoa**和 **_ultoa**函式的別名來存在。 POSIX 名稱已被取代，因為它們不遵循 ISO C 的實作為特定全域函式名稱慣例。根據預設，這些函式會造成淘汰警告[C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)：**此專案的 POSIX 名稱已被取代。請改用符合 ISO C 和 c + + 標準的名稱：** *new_name*。 建議您變更原始程式碼，以使用這些函式的更安全版本， **_itoa_s**、 **_ltoa_s**或 **_ultoa_s**。 如需詳細資訊，請參閱[_itoa_s、_itow_s 函數](itoa-s-itow-s.md)。

針對原始程式碼可攜性，您可能會想要在程式碼中保留 POSIX 名稱。 若要在沒有淘汰警告的情況下使用這些函式，請在包含任何 CRT 標頭之前，先定義 **_CRT_NONSTDC_NO_WARNINGS**和 **_CRT_SECURE_NO_WARNINGS**預處理器宏。 您可以在開發人員命令提示字元中的命令列上執行此動作，方法是將 **/D_CRT_SECURE_NO_WARNINGS**和 **/D_CRT_NONSTDC_NO_WARNINGS**編譯器選項加入**cl**命令。 否則，請在您的原始程式檔中定義宏。 如果您使用先行編譯的標頭，請在先行編譯標頭檔包含檔案的頂端定義宏。 若要在原始程式碼中定義宏，請在包含任何 CRT 標頭之前使用 **#define**指示詞，如下列範例所示：

```C
#define _CRT_NONSTDC_NO_WARNINGS 1
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdlib.h>
```

### <a name="maximum-conversion-count-macros"></a>最大轉換計數宏

為了協助您建立用於轉換的安全緩衝區，CRT 包含一些方便的宏。 這些會定義針對數個通用基底，轉換每個整數類型的最長可能值時所需的緩衝區大小，包括 null 結束字元和正負號字元。 若要確保您的轉換緩衝區夠大，可以在*基數*所指定的基底中接收任何轉換，請在配置緩衝區時使用其中一個已定義的宏。 當您將整數類型轉換成字串時，這有助於防止緩衝區溢位錯誤。 當您的來源中包含 stdlib.h> 或 wchar 時，就會定義這些宏。

若要在字串轉換函式中使用其中一個宏，請宣告適當字元類型的轉換緩衝區，並使用整數類型的宏值，並將基底當做緩衝區維度。 下表列出適用于所列基底之每個函數的宏：

||||
|-|-|-|
|函式|radix|巨集|
|**_itoa**， **_itow**|16<br/>10<br/>8<br/>2|**_MAX_ITOSTR_BASE16_COUNT**<br/>**_MAX_ITOSTR_BASE10_COUNT**<br/>**_MAX_ITOSTR_BASE8_COUNT**<br/>**_MAX_ITOSTR_BASE2_COUNT**|
|**_ltoa**， **_ltow**|16<br/>10<br/>8<br/>2|**_MAX_LTOSTR_BASE16_COUNT**<br/>**_MAX_LTOSTR_BASE10_COUNT**<br/>**_MAX_LTOSTR_BASE8_COUNT**<br/>**_MAX_LTOSTR_BASE2_COUNT**|
|**_ultoa**， **_ultow**|16<br/>10<br/>8<br/>2|**_MAX_ULTOSTR_BASE16_COUNT**<br/>**_MAX_ULTOSTR_BASE10_COUNT**<br/>**_MAX_ULTOSTR_BASE8_COUNT**<br/>**_MAX_ULTOSTR_BASE2_COUNT**|
|**_i64toa**， **_i64tow**|16<br/>10<br/>8<br/>2|**_MAX_I64TOSTR_BASE16_COUNT**<br/>**_MAX_I64TOSTR_BASE10_COUNT**<br/>**_MAX_I64TOSTR_BASE8_COUNT**<br/>**_MAX_I64TOSTR_BASE2_COUNT**|
|**_ui64toa**， **_ui64tow**|16<br/>10<br/>8<br/>2|**_MAX_U64TOSTR_BASE16_COUNT**<br/>**_MAX_U64TOSTR_BASE10_COUNT**<br/>**_MAX_U64TOSTR_BASE8_COUNT**<br/>**_MAX_U64TOSTR_BASE2_COUNT**|

這個範例會使用「轉換計數」宏，將緩衝區定義為足以包含「基底2」中不**帶正負號的長長時間**：

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
|**itoa**、 **ltoa**、 **ultoa**|\<stdlib.h>|
|**_itoa**、 **_ltoa**、 **_ultoa**、 **_i64toa**、 **_ui64toa**|\<stdlib.h>|
|**_itow**、 **_ltow**、 **_ultow**、 **_i64tow**、 **_ui64tow**|\<stdlib.h> 或 \<wchar.h>|

這些函式和宏是 Microsoft 特有的。 如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

這個範例會示範一些整數轉換函數的用法。 請注意，使用 **_CRT_SECURE_NO_WARNINGS**宏來 C4996 無聲警告]。

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
[_itoa_s，_itow_s 函式](itoa-s-itow-s.md)<br/>
