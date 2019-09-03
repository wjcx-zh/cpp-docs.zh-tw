---
title: _rotl8, _rotl16
ms.date: 09/02/2019
f1_keywords:
- _rotl8
- _rotl16
helpviewer_keywords:
- _rotl8 intrinsic
- _rotl16 intrinsic
ms.assetid: 8c519ab6-aef9-4f07-a387-daee8408368f
ms.openlocfilehash: 5dffde2d3f830b6ec4ad43865648c27b1defb593
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218035"
---
# <a name="_rotl8-_rotl16"></a>_rotl8, _rotl16

**Microsoft 專屬**

將輸入值依指定的位置數目，向左旋轉至最高有效位元 (MSB)。

## <a name="syntax"></a>語法

```C
unsigned char _rotl8(
   unsigned char value,
   unsigned char shift
);
unsigned short _rotl16(
   unsigned short value,
   unsigned char shift
);
```

### <a name="parameters"></a>參數

*value*\
在要旋轉的值。

*結*\
在要旋轉的位數。

## <a name="return-value"></a>傳回值

旋轉的值。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`_rotl8`|x86、ARM、x64、ARM64|
|`_rotl16`|x86、ARM、x64、ARM64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

與左移作業不同的是, 在執行左旋轉時, 落在高階的高序位位會移到最不重要的位位置。

## <a name="example"></a>範例

```cpp
// rotl.cpp
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(_rotl8, _rotl16)

int main()
{
    unsigned char c = 'A', c1, c2;

    for (int i = 0; i < 8; i++)
    {
       printf_s("Rotating 0x%x left by %d bits gives 0x%x\n", c,
               i, _rotl8(c, i));
    }

    unsigned short s = 0x12;
    int nBit = 10;

    printf_s("Rotating unsigned short 0x%x left by %d bits gives 0x%x\n",
            s, nBit, _rotl16(s, nBit));
}
```

```Output
Rotating 0x41 left by 0 bits gives 0x41
Rotating 0x41 left by 1 bits gives 0x82
Rotating 0x41 left by 2 bits gives 0x5
Rotating 0x41 left by 3 bits gives 0xa
Rotating 0x41 left by 4 bits gives 0x14
Rotating 0x41 left by 5 bits gives 0x28
Rotating 0x41 left by 6 bits gives 0x50
Rotating 0x41 left by 7 bits gives 0xa0
Rotating unsigned short 0x12 left by 10 bits gives 0x4800
```

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[_rotr8, _rotr16](../intrinsics/rotr8-rotr16.md)\
[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
