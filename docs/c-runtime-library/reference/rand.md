---
title: rand
ms.date: 4/2/2020
api_name:
- rand
- _o_rand
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
- api-ms-win-crt-utility-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- rand
helpviewer_keywords:
- generating pseudorandom numbers
- random numbers, generating
- numbers, pseudorandom
- rand function
- pseudorandom numbers
- numbers, generating pseudorandom
ms.openlocfilehash: 8f2a4d00310671e8ba80055e38e479e348562ac2
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919532"
---
# <a name="rand"></a>rand

使用已知且完全可重現的演算法，產生偽虛擬數位。 此函式有更具程式設計的安全版本可供使用;請參閱[rand_s](rand-s.md)。 **Rand**所產生的數位不會以密碼編譯方式保護。 如需以密碼編譯安全的亂數產生，請使用[rand_s](rand-s.md)或在 c + + 標準程式庫中以[ \<隨機>](../../standard-library/random.md)宣告的函數。

## <a name="syntax"></a>語法

```C
int rand( void );
```

## <a name="return-value"></a>傳回值

**rand**會傳回亂數字，如上所述。 不會傳回錯誤。

## <a name="remarks"></a>備註

**Rand**函數會傳回0到**RAND_MAX** （32767）範圍內的隨機整數。 呼叫**rand**之前，請先使用[srand](srand.md)函數來植入亂數產生器。

**Rand**函式會產生知名的順序，而不適合當做密碼編譯功能使用。 如需以密碼編譯安全的亂數產生，請使用[rand_s](rand-s.md)或在 c + + 標準程式庫中以[ \<隨機>](../../standard-library/random.md)宣告的函數。 如需**rand**問題的相關資訊，以及隨機\<> 如何解決這些缺點，請參閱這段標題為[rand 視為有害](https://channel9.msdn.com/Events/GoingNative/2013/rand-Considered-Harmful)的影片。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**rand**|\<stdlib.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_rand.c
// This program seeds the random-number generator
// with the time, then exercises the rand function.
//

#include <stdlib.h>
#include <stdio.h>
#include <time.h>

void SimpleRandDemo( int n )
{
   // Print n random numbers.
   int i;
   for( i = 0; i < n; i++ )
      printf( "  %6d\n", rand() );
}

void RangedRandDemo( int range_min, int range_max, int n )
{
   // Generate random numbers in the half-closed interval
   // [range_min, range_max). In other words,
   // range_min <= random number < range_max
   int i;
   for ( i = 0; i < n; i++ )
   {
      int u = (double)rand() / (RAND_MAX + 1) * (range_max - range_min)
            + range_min;
      printf( "  %6d\n", u);
   }
}

int main( void )
{
   // Seed the random-number generator with the current time so that
   // the numbers will be different every time we run.
   srand( (unsigned)time( NULL ) );

   SimpleRandDemo( 10 );
   printf("\n");
   RangedRandDemo( -100, 100, 10 );
}
```

```Output
22036
18330
11651
27464
18093
3284
11785
14686
11447
11285

   74
   48
   27
   65
   96
   64
   -5
  -42
  -55
   66
```

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[srand](srand.md)<br/>
[rand_s](rand-s.md)<br/>
