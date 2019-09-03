---
title: __stosq
ms.date: 09/02/2019
f1_keywords:
- __stosq
helpviewer_keywords:
- rep stosq instruction
- stosq instruction
- __stosq intrinsic
ms.assetid: 3ea28297-4369-4c2d-bf0c-91fa539ce209
ms.openlocfilehash: 8b347d595da4cdbf1fefb6244940e262981671e9
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219959"
---
# <a name="__stosq"></a>__stosq

**Microsoft 專屬**

產生存放區字串指令 (`rep stosq`)。

## <a name="syntax"></a>語法

```C
void __stosb(
   unsigned __int64* Destination,
   unsigned __int64 Data,
   size_t Count
);
```

### <a name="parameters"></a>參數

*位置*\
脫銷作業的目的地。

*Data*\
在要儲存的資料。

*計數*\
在要寫入的 quadwords 區塊長度。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__stosq`|AMD64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

結果是將四個*資料*寫入至*目的地*字串中的*Count* quadwords 區塊。

此常式僅可作為內建常式使用。

## <a name="example"></a>範例

```C
// stosq.c
// processor: x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__stosq)

int main()
{
   unsigned __int64 val = 0xFFFFFFFFFFFFI64;
   unsigned __int64 a[10];
   memset(a, 0, sizeof(a));
   __stosq(a+1, val, 2);
   printf("%I64x %I64x %I64x %I64x", a[0], a[1], a[2], a[3]);
}
```

```Output
0 ffffffffffff ffffffffffff 0
```

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
