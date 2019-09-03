---
title: __movsd
ms.date: 09/02/2019
f1_keywords:
- __movsd
helpviewer_keywords:
- rep movsd instruction
- __movsd intrinsic
- movsd instruction
ms.assetid: eb5cccf3-aa76-47f0-b9fc-eeca38fd943f
ms.openlocfilehash: c43f6bdb731abc281d60fe4bc6ecaec1331b9945
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221764"
---
# <a name="__movsd"></a>__movsd

**Microsoft 專屬**

產生 Move String (`rep movsd`) 指令。

## <a name="syntax"></a>語法

```C
void __movsd(
   unsigned long* Destination,
   unsigned long* Source,
   size_t Count
);
```

### <a name="parameters"></a>參數

*位置*\
脫銷作業的目的地。

*Source*\
在作業的來源。

*計數*\
在要複製的雙用字數目。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__movsd`|x86、x64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

結果是會將*來源*所指向的第一個*計數*雙字複製到*目的*字串。

此常式僅可作為內建常式使用。

## <a name="example"></a>範例

```cpp
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

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
