---
title: __movsw
ms.date: 09/02/2019
f1_keywords:
- __movsw
helpviewer_keywords:
- movsw instruction
- rep movsw instruction
- __movsw intrinsic
ms.assetid: db402ad5-7f0e-449a-b0b0-eea9928d6435
ms.openlocfilehash: 67eef7fe0a5b9803650f345740a8c40262cd2014
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221716"
---
# <a name="__movsw"></a>__movsw

**Microsoft 專屬**

產生 Move String (`rep movsw`) 指令。

## <a name="syntax"></a>語法

```C
void __movsw(
   unsigned short* Destination,
   unsigned short* Source,
   size_t Count
);
```

### <a name="parameters"></a>參數

*位置*\
脫銷作業的目的地。

*Source*\
在作業的來源。

*計數*\
在要複製的單字數目。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__movsw`|x86、x64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

結果是會將*來源*所指向的第一個*計數*單字複製到*目的*字串。

此常式僅可作為內建常式使用。

## <a name="example"></a>範例

```cpp
// movsw.cpp
// processor: x86, x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__movsw)

int main()
{
    unsigned short s1[10];
    unsigned short s2[10] = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
    __movsw(s1, s2, 10);

    for (int i = 0; i < 10; i++)
        printf_s("%d ", s1[i]);
    printf_s("\n");
}
```

```Output
0 1 2 3 4 5 6 7 8 9
```

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
