---
title: _rotl、_rotl64、_rotr、_rotr64
description: _Rotl、_rotl64、_rotr 和 _rotr64 的 API 參考;這會將位向左旋轉 (_rotl) 或)  (_rotr。
ms.date: 04/05/2018
api_name:
- _rotr64
- _rotl
- _rotr
- _rotl64
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _rotr64
- rotl64
- _rotl64
- rotr64
- rotr
- _rotr
- _rotl
- rotl
helpviewer_keywords:
- rotl64 function
- _rotl function
- rotr function
- rotr64 function
- _rotr function
- rotl function
- _rotl64 function
- rotating bits
- _rotr64 function
- bits, rotating
ms.assetid: cfce439b-366f-4584-8ab1-d527b13fcfc6
ms.openlocfilehash: d2fb6b2674ed7d50cff63ae45f22af63b0120597
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556589"
---
# <a name="_rotl-_rotl64-_rotr-_rotr64"></a>_rotl、_rotl64、_rotr、_rotr64

將位旋轉至左方 (**_rotl**) 或右 (**_rotr**) 。

## <a name="syntax"></a>語法

```C

unsigned int _rotl(
   unsigned int value,
   int shift
);
unsigned __int64 _rotl64(
   unsigned __int64 value,
   int shift
);
unsigned int _rotr(
   unsigned int value,
   int shift
);
unsigned __int64 _rotr64(
   unsigned __int64 value,
   int shift
);
```

### <a name="parameters"></a>參數

*value*<br/>
要旋轉的值。

*shift*<br/>
要移位的位元數。

## <a name="return-value"></a>傳回值

旋轉的值。 不會傳回錯誤。

## <a name="remarks"></a>備註

**_Rotl**和 **_rotr**函式會依*shift*位旋轉不帶正負號的*值*。 **_rotl** 將值向左旋轉。 **_rotr** 將值向右旋轉。 這兩個函式會將旋轉超出 *value* 一端的位元換行到另一端。

## <a name="requirements"></a>規格需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_rotl**， **_rotl64**|\<stdlib.h>|
|**_rotr**， **_rotr64**|\<stdlib.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

```C
// crt_rot.c
/* This program shifts values to rotate an integer.
*/

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   unsigned val = 0x0fd93;
   __int64 val2 = 0x0101010101010101;

   printf( "0x%4.4x rotated left three times is 0x%4.4x\n",
           val, _rotl( val, 3 ) );
   printf( "0x%4.4x rotated right four times is 0x%4.4x\n",
           val, _rotr( val, 4 ) );

   printf( "%I64x rotated left three times is %I64x\n",
           val2, _rotl64( val2, 3 ) );
   printf( "%I64x rotated right four times is %I64x\n",
           val2, _rotr64( val2, 4 ) );
}
```

### <a name="output"></a>輸出

```Output
0xfd93 rotated left three times is 0x7ec98
0xfd93 rotated right four times is 0x30000fd9
101010101010101 rotated left three times is 808080808080808
101010101010101 rotated right four times is 1010101010101010
```

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[_lrotl、_lrotr](lrotl-lrotr.md)<br/>
