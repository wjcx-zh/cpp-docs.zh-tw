---
title: rand
description: 適用于 rand 的 API 參考，它會使用已知且可完全重現的演算法產生亂數。
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
ms.openlocfilehash: 50c4f921c81ecad00abb19e6ce50158d450b170e
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555328"
---
# <a name="rand"></a>rand

使用已知且可完全重現的演算法產生亂數。 此函式有更多程式設計的安全版本可供使用;請參閱 [rand_s](rand-s.md)。 由 **rand** 產生的數位不是密碼編譯安全的。 如需更多密碼編譯安全亂數產生，請使用 [rand_s](rand-s.md) 或在的 c + + 標準程式庫中宣告的函數 [\<random>](../../standard-library/random.md) 。

## <a name="syntax"></a>語法

```C
int rand( void );
```

## <a name="return-value"></a>傳回值

如上面所述， **rand**會傳回虛擬亂數。 不會傳回錯誤。

## <a name="remarks"></a>備註

**Rand**函數會傳回範圍0中的隨機整數，以**RAND_MAX** (32767) 。 在呼叫**rand**之前，請先使用[>srand](srand.md)函式來植入虛擬亂數產生器。

**Rand**函式會產生已知的順序，並不適合做為密碼編譯函式使用。 如需更多密碼編譯安全亂數產生，請使用 [rand_s](rand-s.md) 或在的 c + + 標準程式庫中宣告的函數 [\<random>](../../standard-library/random.md) 。 如需有關 **rand** 有哪些錯誤，以及如何 \<random> 解決這些缺點的詳細資訊，請參閱這段影片，其會將 [rand 視為有害](https://channel9.msdn.com/Events/GoingNative/2013/rand-Considered-Harmful)。

依預設，此函式的全域狀態範圍為應用程式。 若要變更此項，請參閱 [CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>規格需求

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
