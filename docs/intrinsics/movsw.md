---
title: __movsw
ms.date: 11/04/2016
f1_keywords:
- __movsw
helpviewer_keywords:
- movsw instruction
- rep movsw instruction
- __movsw intrinsic
ms.assetid: db402ad5-7f0e-449a-b0b0-eea9928d6435
ms.openlocfilehash: 4bb8a6411c3700b3338fb7d5bc76884f84bb2413
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50453609"
---
# <a name="movsw"></a>__movsw

**Microsoft 專屬**

產生的移動的字串 (`rep movsw`) 指令。

## <a name="syntax"></a>語法

```
void __movsw( 
   unsigned short* Dest, 
   unsigned short* Source, 
   size_t Count 
);
```

#### <a name="parameters"></a>參數

*目的地*<br/>
[out]作業的目的地。

*來源*<br/>
[in]作業的來源。

*計數*<br/>
[in]若要複製的字組數目。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__movsw`|x86、x64|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

結果是第一個`Count`所指向的字`Source`複製到`Dest`字串。

此常式僅可作為內建常式使用。

## <a name="example"></a>範例

```
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

[編譯器內建](../intrinsics/compiler-intrinsics.md)