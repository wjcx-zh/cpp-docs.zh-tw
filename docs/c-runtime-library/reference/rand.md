---
title: rand | Microsoft Docs
ms.custom: 
ms.date: 1/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: rand
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
f1_keywords: rand
dev_langs: C++
helpviewer_keywords:
- generating pseudorandom numbers
- random numbers, generating
- numbers, pseudorandom
- rand function
- pseudorandom numbers
- numbers, generating pseudorandom
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: aada39e6ea3de3cae65642d29fa1b5ce4bad098e
ms.sourcegitcommit: a5d8f5b92cb5e984d5d6c9d67fe8a1241f3fe184
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2018
---
# <a name="rand"></a>rand

使用已知的而且完全可重現的演算法來產生亂數。 此函式多以程式設計方式安全版本可用;請參閱[rand_s](../../c-runtime-library/reference/rand-s.md)。 所產生的數字`rand`是不安全的密碼編譯。 多個密碼編譯安全隨機產生的請使用`rand_s`函式中的 c + + 標準程式庫中所宣告或[\<隨機 >](../../standard-library/random.md)。

## <a name="syntax"></a>語法

```C
int rand( void );
```

## <a name="return-value"></a>傳回值

`rand` 傳回虛擬亂數，如上所述。 不會傳回錯誤。

## <a name="remarks"></a>備註

`rand` 函式會傳回虛擬隨機整數，範圍介於 0 到 `RAND_MAX` (32767)。 使用 [srand](../../c-runtime-library/reference/srand.md) 函式可植入虛擬亂數產生器，然後再呼叫 `rand`。

`rand`函式會產生熟知的順序並不適合做為密碼編譯功能。 多個密碼編譯安全隨機產生的請使用`rand_s`函式中的 c + + 標準程式庫中所宣告或[\<隨機 >](../../standard-library/random.md)。 如需 `rand()` 所發生錯誤以及 `<random>` 如何解決這些缺點的詳細資訊，請參閱[本影片](http://go.microsoft.com/fwlink/?LinkId=397615)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|`rand`|\<stdlib.h>|

如需其他相容性資訊，請參閱＜簡介＞中的 [相容性](../../c-runtime-library/compatibility.md) 。

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

[浮點支援](../../c-runtime-library/floating-point-support.md)  
[srand](../../c-runtime-library/reference/srand.md)  
[rand_s](../../c-runtime-library/reference/rand-s.md)  