---
title: __stosw
ms.date: 09/02/2019
f1_keywords:
- __stosw
helpviewer_keywords:
- stosw instruction
- __stosw intrinsic
- rep stosw instruction
ms.assetid: 7620fd1d-dba5-40e3-8e07-01aa68895133
ms.openlocfilehash: 5fd29bbf1aebba115670fc1bc35e0d8cbe29c7ad
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219922"
---
# <a name="__stosw"></a>__stosw

**Microsoft 專屬**

產生存放區字串指令 (`rep stosw`)。

## <a name="syntax"></a>語法

```C
void __stosw(
   unsigned short* Destination,
   unsigned short Data,
   size_t Count
);
```

### <a name="parameters"></a>參數

*位置*\
脫銷作業的目的地。

*Data*\
在要儲存的資料。

*計數*\
在要寫入的單字區塊長度。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__stosw`|x86、x64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

結果就是將文字*資料*寫入至*目的*字串中的*Count*個單字區塊。

此常式僅可作為內建常式使用。

## <a name="example"></a>範例

```C
// stosw.c
// processor: x86, x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__stosw)

int main()
{
    unsigned short val = 128;
    unsigned short a[100];
    memset(a, 0, sizeof(a));
    __stosw(a+10, val, 2);
    printf_s("%u %u %u %u", a[9], a[10], a[11], a[12]);
}
```

```Output
0 128 128 0
```

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
