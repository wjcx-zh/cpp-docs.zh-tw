---
title: memchr、wmemchr | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- wmemchr
- memchr
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
apitype: DLLExport
f1_keywords:
- memchr
- wmemchr
dev_langs:
- C++
helpviewer_keywords:
- memchr function
- wmemchr function
ms.assetid: 5a348581-28f1-4256-8434-687245f7fc9f
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2eb092abaa1e49c13ca05066de98b533507b4421
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="memchr-wmemchr"></a>memchr、wmemchr

在緩衝區中尋找字元。

## <a name="syntax"></a>語法

```C
void *memchr(
   const void *buffer,
   int c,
   size_t count
); // C only
void *memchr(
   void *buffer,
   int c,
   size_t count
); // C++ only
const void *memchr(
   const void *buffer,
   int c,
   size_t count
); // C++ only
wchar_t *wmemchr(
   const wchar_t * buffer,
   wchar_t c,
   size_t count
); // C only
wchar_t *wmemchr(
   wchar_t * buffer,
   wchar_t c,
   size_t count
); // C++ only
const wchar_t *wmemchr(
   const wchar_t * buffer,
   wchar_t c,
   size_t count
); // C++ only
```

### <a name="parameters"></a>參數

*buffer*<br/>
緩衝區的指標。

*C*<br/>
要尋找的字元。

*count*<br/>
要檢查的字元數。

## <a name="return-value"></a>傳回值

如果成功，傳回的第一個位置的指標*c*中*緩衝區*。 否則它會傳回**NULL**。

## <a name="remarks"></a>備註

**memchr**和**wmemchr**尋找第一個出現*c*在第一個*計數*位元組*緩衝區*。 它會停止在找到時*c*或當其已簽入第一個*計數*位元組。

在 C 中，這些函數會使用 * * const * * 的第一個引數的指標。 在 C++ 中，可使用兩個多載。 取得指標的多載 * * const * * 將指標傳回至**const **; 版本採用一個指向非**const * * 將指標傳回至非**const **。如果兩個使用者定義巨集 _CRT_CONST_CORRECT_OVERLOADS **const * * 和非-** const * * 這些函式的版本可供使用。如果您需要非**const * * 這兩個 c + + overloadsin c + + 行為定義符號 _CONST_RETURN。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**memchr**|\<memory.h> 或 \<string.h>|
|**wmemchr**|\<wchar.h>|

如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

```C
// crt_memchr.c

#include <memory.h>
#include <stdio.h>

int  ch = 'r';
char str[] =    "lazy";
char string[] = "The quick brown dog jumps over the lazy fox";
char fmt1[] =   "         1         2         3         4         5";
char fmt2[] =   "12345678901234567890123456789012345678901234567890";

int main( void )
{
   char *pdest;
   int result;
   printf( "String to be searched:\n             %s\n", string );
   printf( "             %s\n             %s\n\n", fmt1, fmt2 );

   printf( "Search char: %c\n", ch );
   pdest = memchr( string, ch, sizeof( string ) );
   result = (int)(pdest - string + 1);
   if ( pdest != NULL )
      printf( "Result:      %c found at position %d\n", ch, result );
   else
      printf( "Result:      %c not found\n" );
}
```

### <a name="output"></a>輸出

```Output
String to be searched:
             The quick brown dog jumps over the lazy fox
                      1         2         3         4         5
             12345678901234567890123456789012345678901234567890

Search char: r
Result:      r found at position 12
```

## <a name="see-also"></a>另請參閱

[緩衝區操作](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memcmp、wmemcmp](memcmp-wmemcmp.md)<br/>
[memcpy、wmemcpy](memcpy-wmemcpy.md)<br/>
[memset、wmemset](memset-wmemset.md)<br/>
[strchr、wcschr、_mbschr、_mbschr_l](strchr-wcschr-mbschr-mbschr-l.md)<br/>
