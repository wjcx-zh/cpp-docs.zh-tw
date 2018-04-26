---
title: _itoa、 _itow 函式 |Microsoft 文件
ms.custom: ''
ms.date: 03/21/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 34069bd8866e38faa2cade18e44e16eda4154a40
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="itoa-itoa-ltoa-ltoa-ultoa-ultoa-i64toa-ui64toa-itow-ltow-ultow-i64tow-ui64tow"></a>itoa _itoa、 ltoa、 _ltoa、 ultoa、 _ultoa、 _i64toa、 _ui64toa、 _itow、 _ltow、 _ultow、 _i64tow、 _ui64tow

將整數轉換成字串。 這些函式更安全的版本可用;請參閱[_itoa_s、 _itow_s 函式](itoa-s-itow-s.md)。

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

// These Posix versions of the functions have deprecated names:
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

*buffer*<br/>
保留轉換結果的緩衝區。

*radix*<br/>
若要使用的轉換的基底*值*，這必須在範圍 2-36。

*size*<br/>
字元類型的單位的緩衝區長度。 這個參數會從推斷*緩衝區*c + + 中的引數。

## <a name="return-value"></a>傳回值

所有這些函式傳回的指標*緩衝區*。 不會傳回錯誤。

## <a name="remarks"></a>備註

**_Itoa**， **_ltoa**， **_ultoa**， **_i64toa**，和 **_ui64toa**函數會將轉換的數字指定*值*引數來以 null 結束的字元字串並儲存結果 (最多 33 字元 **_itoa**， **_ltoa**，和 **_ultoa**，如 65 **_i64toa**和 **_ui64toa**) 中*緩衝區*。 如果*基數*等於 10 和*值*是負數，預存字串的第一個字元是減號 (**-**)。 **_Itow**， **_ltow**， **_ultow**， **_i64tow**，和 **_ui64tow**函式是寬字元新版 **_itoa**， **_ltoa**， **_ultoa**， **_i64toa**，和 **_ui64toa**，分別。

> [!IMPORTANT]
> 這些函式可寫入超過結尾的緩衝區太小。 若要防止緩衝區溢位，請確認*緩衝區*夠大，無法保存已轉換的數字加上尾端的 null 字元和符號字元。 不當使用這些函式會造成嚴重的安全性問題的程式碼。

因為其可能會有安全性問題，根據預設，這些函式會導致取代警告[C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md):**此函式或變數可能不安全。請考慮使用** *safe_function* **改為。若要停用已被取代，請使用 _CRT_SECURE_NO_WARNINGS。** 我們建議您變更使用您的原始程式碼*safe_function*警告訊息所建議。 更安全的函式不會寫入更多超過指定的緩衝區大小的字元。 如需詳細資訊，請參閱[_itoa_s、 _itow_s 函式](itoa-s-itow-s.md)。

若要使用這些函式已被取代警告，定義 **_CRT_SECURE_NO_WARNINGS**之前 CRT 標頭加入前置處理器巨集。 您可以在開發人員命令提示字元中的命令列上加 **/D_CRT_SECURE_NO_WARNINGS**編譯器選項以**cl**命令。 否則，在原始程式檔中定義巨集。 如果您使用先行編譯標頭，定義巨集頂端的 先行編譯標頭包含檔案，通常為 stdafx.h。 若要在您的程式碼中定義巨集，請使用 **#define**指示詞再包含任何 CRT 標頭，如此範例所示：

```C
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdlib.h>
```

在 c + +，這些函式具有樣板多載，叫用其更安全的對應版本。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

Posix 名稱**itoa**， **ltoa**，和**ultoa**存在做為別名的 **_itoa**， **_ltoa**，和 **_ultoa**函式。 因為它們不會遵循 ISO C 的實作特定函式名稱慣例，已被取代的 Posix 名稱根據預設，這些函式會造成已被取代警告[C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md):**此項目的 POSIX 名稱已被取代。相反地，使用 ISO C 和 c + + 一致的名稱：** *new_name*。 我們建議您變更使用更安全的版本，這些函式，您的原始程式碼 **_itoa_s**， **_ltoa_s**，或 **_ultoa_s**。 如需詳細資訊，請參閱[_itoa_s、 _itow_s 函式](itoa-s-itow-s.md)。

來源的程式碼可攜性，您可能會想要保留在程式碼中的 Posix 名稱。 若要使用這些函式已被取代警告，同時定義 **_CRT_NONSTDC_NO_WARNINGS**和 **_CRT_SECURE_NO_WARNINGS**之前 CRT 標頭加入前置處理器巨集。 您可以在開發人員命令提示字元中的命令列上加 **/D_CRT_SECURE_NO_WARNINGS**和 **/D_CRT_NONSTDC_NO_WARNINGS**編譯器選項，以**cl**命令。 否則，在原始程式檔中定義的巨集。 如果您使用先行編譯標頭，定義的巨集頂端的 先行編譯標頭包含檔案，通常 stdafx.h。 若要在您的程式碼中定義巨集，請使用 **#define**指示詞再包含任何 CRT 標頭，如此範例所示：

```C
#define _CRT_NONSTDC_NO_WARNINGS 1
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdlib.h>
```

### <a name="maximum-conversion-count-macros"></a>最大轉換計數巨集

為了協助您建立安全的轉換緩衝區，CRT 包含一些方便的巨集。 這些定義的每個整數型別，包括 null 結束字元的最長可能的值轉換所需的緩衝區大小，並登入數個通用基底的字元。 若要確保轉換緩衝區不夠大，無法接收任何轉換中所指定的基底*基數*，配置的緩衝區時，使用下列其中一種定義巨集。 這有助於防止緩衝區溢位錯誤，當您將整數類資料類型轉換成字串。 這些巨集會定義當 stdlib.h 或 wchar.h 納入您的來源。

若要使用這些巨集的其中一個字串轉換函式中，宣告適當的字元類型的轉換緩衝區和使用巨集值的整數型別與基底做為緩衝區的維度。 下表列出適用於每個列出的基底的函式的巨集：

||||
|-|-|-|
|函式|radix|巨集|
|**_itoa**， **_itow**|16<br/>10<br/>8<br/>2|**_MAX_ITOSTR_BASE16_COUNT**<br/>**_MAX_ITOSTR_BASE10_COUNT**<br/>**_MAX_ITOSTR_BASE8_COUNT**<br/>**_MAX_ITOSTR_BASE2_COUNT**|
|**_ltoa**， **_ltow**|16<br/>10<br/>8<br/>2|**_MAX_LTOSTR_BASE16_COUNT**<br/>**_MAX_LTOSTR_BASE10_COUNT**<br/>**_MAX_LTOSTR_BASE8_COUNT**<br/>**_MAX_LTOSTR_BASE2_COUNT**|
|**_ultoa**， **_ultow**|16<br/>10<br/>8<br/>2|**_MAX_ULTOSTR_BASE16_COUNT**<br/>**_MAX_ULTOSTR_BASE10_COUNT**<br/>**_MAX_ULTOSTR_BASE8_COUNT**<br/>**_MAX_ULTOSTR_BASE2_COUNT**|
|**_i64toa**， **_i64tow**|16<br/>10<br/>8<br/>2|**_MAX_I64TOSTR_BASE16_COUNT**<br/>**_MAX_I64TOSTR_BASE10_COUNT**<br/>**_MAX_I64TOSTR_BASE8_COUNT**<br/>**_MAX_I64TOSTR_BASE2_COUNT**|
|**_ui64toa**， **_ui64tow**|16<br/>10<br/>8<br/>2|**_MAX_U64TOSTR_BASE16_COUNT**<br/>**_MAX_U64TOSTR_BASE10_COUNT**<br/>**_MAX_U64TOSTR_BASE8_COUNT**<br/>**_MAX_U64TOSTR_BASE2_COUNT**|

這個範例會使用轉換計數巨集來定義的緩衝區大小足以包含**unsigned long long**基底 2:

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

|常式|必要的標頭|
|-------------|---------------------|
|**itoa**， **ltoa**， **ultoa**|\<stdlib.h>|
|**_itoa**， **_ltoa**， **_ultoa**， **_i64toa**， **_ui64toa**|\<stdlib.h>|
|**_itow**， **_ltow**， **_ultow**， **_i64tow**， **_ui64tow**|\<stdlib.h> 或 \<wchar.h>|

這些函式和巨集是 Microsoft 特定的。 如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

此範例將示範如何使用部分的整數轉換函式。 請注意使用 **_CRT_SECURE_NO_WARNINGS**巨集，以警告 C4996 轉為無回應。

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
[_itoa_s、 _itow_s 函式](itoa-s-itow-s.md)<br/>
