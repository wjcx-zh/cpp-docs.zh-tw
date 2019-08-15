---
title: rand_s
ms.date: 1/02/2018
apiname:
- rand_s
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
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- rand_s
helpviewer_keywords:
- generating pseudorandom numbers
- random numbers, cryptographically secure
- random numbers, generating
- rand_s function
- numbers, pseudorandom
- cryptographically secure random numbers
- pseudorandom numbers
- numbers, generating pseudorandom
ms.openlocfilehash: 7a2c57713d4b455971f24b64dc124862749e927a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69499555"
---
# <a name="rand_s"></a>rand_s

產生虛擬亂數。 這是更安全的函數[rand](rand.md)版本, 其中包含[CRT 中的安全性功能中](../../c-runtime-library/security-features-in-the-crt.md)所述的安全性增強功能。

## <a name="syntax"></a>語法

```C
errno_t rand_s(unsigned int* randomValue);
```

### <a name="parameters"></a>參數

*randomValue*<br/>
指向用來保存所產生值的整數指標。

## <a name="return-value"></a>傳回值

如果成功則為零，否則為錯誤碼。 如果輸入指標_randomValue_是 null 指標, 此函式會叫用不正確參數處理常式, 如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行, 此函式會傳回**EINVAL** , 並將**Errno**設定為**EINVAL**。 如果函式因為任何其他原因而失敗, 則 *_randomValue_會設定為0。

## <a name="remarks"></a>備註

**Rand_s**函數會將0到**UINT_MAX**範圍內的隨機整數寫入輸入指標。 **Rand_s**函數會使用作業系統來產生密碼編譯安全的亂數字。 它不會使用[srand](srand.md)函數所產生的種子, 也不會影響[rand](rand.md)所使用的亂數字序列。

**Rand_s**函數需要在要宣告之函式的包含語句之前定義常數 **_CRT_RAND_S** , 如下列範例所示:

```C
#define _CRT_RAND_S
#include <stdlib.h>
```

**rand_s**取決於[RtlGenRandom](/windows/win32/api/ntsecapi/nf-ntsecapi-rtlgenrandom) API, 這僅適用于 Windows XP 和更新版本。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**rand_s**|\<stdlib.h>|

如需詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_rand_s.c
// This program illustrates how to generate random
// integer or floating point numbers in a specified range.

// Remembering to define _CRT_RAND_S prior
// to inclusion statement.
#define _CRT_RAND_S

#include <stdlib.h>
#include <stdio.h>
#include <limits.h>

int main( void )
{
    int             i;
    unsigned int    number;
    double          max = 100.0;
    errno_t         err;

    // Display 10 random integers in the range [ 1,10 ].
    for( i = 0; i < 10;i++ )
    {
        err = rand_s( &number );
        if (err != 0)
        {
            printf_s("The rand_s function failed!\n");
        }
        printf_s( "  %u\n", (unsigned int) ((double)number /
                       ((double) UINT_MAX + 1 ) * 10.0) + 1);
    }

    printf_s("\n");

    // Display 10 random doubles in [0, max).
    for (i = 0; i < 10;i++ )
    {
        err = rand_s( &number );
        if (err != 0)
        {
            printf_s("The rand_s function failed!\n");
        }
        printf_s( "  %g\n", (double) number /
                          ((double) UINT_MAX + 1) * max );
    }
}
```

### <a name="sample-output"></a>範例輸出

```Output
10
4
5
2
8
2
5
6
1
1

32.6617
29.4471
11.5413
6.41924
20.711
60.2878
61.0094
20.1222
80.9192
65.0712
```

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[rand](rand.md)<br/>
[srand](srand.md)<br/>
