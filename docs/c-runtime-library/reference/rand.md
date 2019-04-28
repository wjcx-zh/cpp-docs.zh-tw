---
title: rand
ms.date: 1/02/2018
apiname:
- rand
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
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- rand
helpviewer_keywords:
- generating pseudorandom numbers
- random numbers, generating
- numbers, pseudorandom
- rand function
- pseudorandom numbers
- numbers, generating pseudorandom
ms.openlocfilehash: 868c6239ac1b86dfc9ac72cc8cc83d1ba3002b4a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62357768"
---
# <a name="rand"></a>rand

使用已知且完全可重現的演算法，以產生亂數。 此函式程式設計更安全版本可用;請參閱[rand_s](rand-s.md)。 所產生的數字**rand**是不安全的密碼編譯。 多個密碼編譯安全的亂數產生，請使用[rand_s](rand-s.md)中所宣告的函式或C++中的標準程式庫[\<隨機 >](../../standard-library/random.md)。

## <a name="syntax"></a>語法

```C
int rand( void );
```

## <a name="return-value"></a>傳回值

**rand**傳回虛擬亂數，如上所述。 不會傳回錯誤。

## <a name="remarks"></a>備註

**Rand**函式會傳回虛擬隨機整數的範圍介於 0 到**RAND_MAX** (32767)。 使用[srand](srand.md)函式，來植入亂數產生器，然後再呼叫**rand**。

**Rand**函式會產生熟知的順序，並不適合做為密碼編譯的函式。 多個密碼編譯安全的亂數產生，請使用[rand_s](rand-s.md)中所宣告的函式或C++中的標準程式庫[\<隨機 >](../../standard-library/random.md)。 如需何不妥**rand**以及如何\<隨機 > 解決這些缺點，請參閱這段影片中標題為[rand 視為有害](https://channel9.msdn.com/Events/GoingNative/2013/rand-Considered-Harmful)。

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
