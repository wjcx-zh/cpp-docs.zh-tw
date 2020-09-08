---
title: _lrotl、_lrotr
description: '_Lrotl 和 _lrotr 的 API 參考;這會將位向左旋轉 (_lrotl) 或)  (_lrotr。 '
ms.date: 04/04/2018
api_name:
- _lrotl
- _lrotr
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
- lrotr
- lrotl
- _lrotr
- _lrotl
helpviewer_keywords:
- lrotl function
- bits
- _lrotr function
- lrotr function
- rotating bits
- _lrotl function
- bits, rotating
ms.assetid: d42f295b-35f9-49d2-9ee4-c66896ffe68e
ms.openlocfilehash: ccd14f7aa6ba3c1278063593aecee20c6789110d
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555003"
---
# <a name="_lrotl-_lrotr"></a>_lrotl、_lrotr

將位旋轉至左方 (**_lrotl**) 或右 (**_lrotr**) 。

## <a name="syntax"></a>語法

```C
unsigned long _lrotl( unsigned long value, int shift );
unsigned long _lrotr( unsigned long value, int shift );
```

### <a name="parameters"></a>參數

*value*<br/>
要旋轉的值。

*shift*<br/>
*value* 要移位的位元數。

## <a name="return-value"></a>傳回值

這兩個函式會傳回旋轉的值。 不會傳回錯誤。

## <a name="remarks"></a>備註

**_Lrotl**和 **_lrotr**函數會以*shift*位旋轉*值*。 **_lrotl** 將值向左旋轉，以取得更高的位。 **_lrotr** 將值向右旋轉，較不重要的位。 這兩個函式會將旋轉超出 *value* 一端的位元換行到另一端。

## <a name="requirements"></a>規格需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_lrotl**， **_lrotr**|\<stdlib.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_lrot.c

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   unsigned long val = 0x0fac35791;

   printf( "0x%8.8lx rotated left eight bits is 0x%8.8lx\n",
            val, _lrotl( val, 8 ) );
   printf( "0x%8.8lx rotated right four bits is 0x%8.8lx\n",
            val, _lrotr( val, 4 ) );
}
```

```Output
0xfac35791 rotated left eight bits is 0xc35791fa
0xfac35791 rotated right four bits is 0x1fac3579
```

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[_rotl、_rotl64、_rotr、_rotr64](rotl-rotl64-rotr-rotr64.md)<br/>
