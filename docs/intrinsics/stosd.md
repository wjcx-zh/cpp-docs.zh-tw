---
title: __stosd
ms.date: 09/02/2019
f1_keywords:
- __stosd
helpviewer_keywords:
- stosd instruction
- rep stosd instruction
- __stosd intrinsic
ms.assetid: 03104247-1cea-49f6-b6f8-287917bf5680
ms.openlocfilehash: c46bb124390ff23d79361c66530493c48faf3f0a
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219974"
---
# <a name="__stosd"></a>__stosd

**Microsoft 專屬**

產生存放區字串指令 (`rep stosd`)。

## <a name="syntax"></a>語法

```C
void __stosd(
   unsigned long* Destination,
   unsigned long Data,
   size_t Count
);
```

### <a name="parameters"></a>參數

*位置*\
脫銷作業的目的地。

*Data*\
在要儲存的資料。

*計數*\
在要寫入的雙列區塊長度。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__stosd`|x86、x64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

結果是在*目的地*所指向的記憶體位置上, 將雙量*資料*寫入至*計數*中的一區塊。

此常式僅可作為內建常式使用。

## <a name="example"></a>範例

```C
// stosd.c
// processor: x86, x64

#include <stdio.h>
#include <memory.h>
#include <intrin.h>

#pragma intrinsic(__stosd)

int main()
{
    unsigned long val = 99999;
    unsigned long a[10];

    memset(a, 0, sizeof(a));
    __stosd(a+1, val, 2);

printf_s( "%u %u %u %u",
              a[0], a[1], a[2], a[3]);
}
```

```Output
0 99999 99999 0
```

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
