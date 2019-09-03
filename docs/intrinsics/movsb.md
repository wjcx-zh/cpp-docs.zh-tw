---
title: __movsb
ms.date: 09/02/2019
f1_keywords:
- __movsb
helpviewer_keywords:
- movsb instruction
- rep movsb instruction
- __movsb intrinsic
ms.assetid: ba5469f6-f797-4cd2-bee8-74c7666c26d4
ms.openlocfilehash: ca06fc9114f6e824a690cc4e612c21d705a485cd
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217274"
---
# <a name="__movsb"></a>__movsb

**Microsoft 專屬**

產生 Move String (`rep movsb`) 指令。

## <a name="syntax"></a>語法

```C
void __movsb(
   unsigned char* Destination,
   unsigned const char* Source,
   size_t Count
);
```

### <a name="parameters"></a>參數

*位置*\
脫銷複製之目的地的指標。

*Source*\
在複製之來源的指標。

*計數*\
在要複製的位元組數目。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__movsb`|x86、x64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

結果是會將所指向`Count` `Source`的前個位元組複製到`Destination`字串。

此常式僅可作為內建常式使用。

## <a name="example"></a>範例

```cpp
// movsb.cpp
// processor: x86, x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__movsb)

int main()
{
    unsigned char s1[100];
    unsigned char s2[100] = "A big black dog.";
    __movsb(s1, s2, 100);

    printf_s("%s %s", s1, s2);
}
```

```Output
A big black dog. A big black dog.
```

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
