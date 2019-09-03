---
title: __stosb
ms.date: 09/02/2019
f1_keywords:
- __stosb
helpviewer_keywords:
- rep stosb instruction
- __stosb intrinsic
- stosb instruction
ms.assetid: 634589ed-2da3-439b-a381-a214d89bf10c
ms.openlocfilehash: edf74da4c8b5aa97e542d89f55b3ed8411db9bac
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221221"
---
# <a name="__stosb"></a>__stosb

**Microsoft 專屬**

產生存放區字串指令 (`rep stosb`)。

## <a name="syntax"></a>語法

```C
void __stosb(
   unsigned char* Destination,
   unsigned char Data,
   size_t Count
);
```

### <a name="parameters"></a>參數

*位置*\
脫銷作業的目的地。

*Data*\
在要儲存的資料。

*計數*\
在要寫入的位元組區塊長度。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__stosb`|x86、x64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

結果是字元*資料*會寫入至*目的地*字串中的*Count*個位元組區塊。

此常式僅可作為內建常式使用。

## <a name="example"></a>範例

```C
// stosb.c
// processor: x86, x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__stosb)

int main()
{
    unsigned char c = 0x40; /* '@' character */
    unsigned char s[] = "*********************************";

    printf_s("%s\n", s);
    __stosb((unsigned char*)s+1, c, 6);
    printf_s("%s\n", s);

}
```

```Output
*********************************
*@@@@@@**************************
```

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
