---
title: __stosb
ms.date: 11/04/2016
f1_keywords:
- __stosb
helpviewer_keywords:
- rep stosb instruction
- __stosb intrinsic
- stosb instruction
ms.assetid: 634589ed-2da3-439b-a381-a214d89bf10c
ms.openlocfilehash: 679f1a892a6ee5b458a05d1577ecf766bed385dd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390278"
---
# <a name="stosb"></a>__stosb

**Microsoft 專屬**

產生的存放區的字串指示 (`rep stosb`)。

## <a name="syntax"></a>語法

```
void __stosb(
   unsigned char* Dest,
   unsigned char Data,
   size_t Count
);
```

#### <a name="parameters"></a>參數

*目的地*<br/>
[out]作業的目的地。

*Data*<br/>
[in]要儲存的資料。

*計數*<br/>
[in]要寫入的位元組區塊的長度。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__stosb`|x86、x64|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

結果是，字元`Data`寫入至區塊`Count`中的位元組`Dest`字串。

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

[編譯器內建](../intrinsics/compiler-intrinsics.md)