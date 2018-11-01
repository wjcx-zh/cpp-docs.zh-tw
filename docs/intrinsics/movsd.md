---
title: __movsd
ms.date: 11/04/2016
f1_keywords:
- __movsd
helpviewer_keywords:
- rep movsd instruction
- __movsd intrinsic
- movsd instruction
ms.assetid: eb5cccf3-aa76-47f0-b9fc-eeca38fd943f
ms.openlocfilehash: 6760904f4eaa6ee32cf9326638ab68f728db45d5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50628588"
---
# <a name="movsd"></a>__movsd

**Microsoft 專屬**

產生的移動的字串 (`rep movsd`) 指令。

## <a name="syntax"></a>語法

```
void __movsd( 
   unsigned long* Dest, 
   unsigned long* Source, 
   size_t Count 
);
```

#### <a name="parameters"></a>參數

*目的地*<br/>
[out]作業的目的地。

*來源*<br/>
[in]作業的來源。

*計數*<br/>
[in]若要複製的雙字組數目。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__movsd`|x86、x64|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

結果是第一個`Count`雙字組所指`Source`複製到`Dest`字串。

此常式僅可作為內建常式使用。

## <a name="example"></a>範例

```
// movsd.cpp
// processor: x86, x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__movsd)

int main()
{
    unsigned long a1[10];
    unsigned long a2[10] = {950, 850, 750, 650, 550, 450, 350,
                            250, 150, 50};
    __movsd(a1, a2, 10);

    for (int i = 0; i < 10; i++)
        printf_s("%d ", a1[i]);
    printf_s("\n");
}
```

```Output
950 850 750 650 550 450 350 250 150 50
```

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)