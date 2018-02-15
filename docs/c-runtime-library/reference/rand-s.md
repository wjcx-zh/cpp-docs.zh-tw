---
title: rand_s | Microsoft Docs
ms.custom: 
ms.date: 1/02/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- generating pseudorandom numbers
- random numbers, cryptographically secure
- random numbers, generating
- rand_s function
- numbers, pseudorandom
- cryptographically secure random numbers
- pseudorandom numbers
- numbers, generating pseudorandom
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2438b2ced054667a658f8f31a37c9a62112debc6
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="rands"></a>rand_s

產生虛擬亂數。 這是更安全的函式版本[rand](../../c-runtime-library/reference/rand.md)，具有安全性增強功能中所述[CRT 中安全性功能](../../c-runtime-library/security-features-in-the-crt.md)。 

## <a name="syntax"></a>語法

```C
errno_t rand_s(unsigned int* randomValue);
```

### <a name="parameters"></a>參數

*randomValue*  
用於儲存產生的值為整數指標。

## <a name="return-value"></a>傳回值

如果成功則為零，否則為錯誤碼。 如果輸入的指標_機會也很小_為 null 指標，函式叫用無效參數處理常式中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，函式會傳回 `EINVAL`，並將 `errno` 設為 `EINVAL`。 如果此函數失敗的任何其他原因，*_機會也很小_設為 0。

## <a name="remarks"></a>備註

`rand_s` 函式會將範圍介於 0 到 `UINT_MAX` 的虛擬隨機整數寫入輸入指標。 `rand_s` 函式使用作業系統來產生密碼編譯安全的亂數。 它不會使用 [srand](../../c-runtime-library/reference/srand.md) 函式所產生的種子，也不會影響 `rand` 使用的亂數順序。

`rand_s` 函式需要先定義常數 `_CRT_RAND_S`，再定義要宣告之函式的包含陳述式，如下列範例所示︰

```C
#define _CRT_RAND_S
#include <stdlib.h>
```

`rand_s` 取決於 [RtlGenRandom](http://msdn.microsoft.com/library/windows/desktop/aa387694) API，這只能在 Windows XP 及更新版本使用。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|`rand_s`|\<stdlib.h>|

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

[浮點支援](../../c-runtime-library/floating-point-support.md)  
[rand](../../c-runtime-library/reference/rand.md)  
[srand](../../c-runtime-library/reference/srand.md)  
