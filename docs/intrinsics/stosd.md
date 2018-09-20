---
title: __stosd |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __stosd
dev_langs:
- C++
helpviewer_keywords:
- stosd instruction
- rep stosd instruction
- __stosd intrinsic
ms.assetid: 03104247-1cea-49f6-b6f8-287917bf5680
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8bb0d75cc4af033bf1bc942a918beecf2aedf911
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396138"
---
# <a name="stosd"></a>__stosd

**Microsoft 專屬**

產生的存放區的字串指示 (`rep stosd`)。

## <a name="syntax"></a>語法

```
void __stosd( 
   unsigned long* Dest, 
   unsigned long Data, 
   size_t Count 
);
```

#### <a name="parameters"></a>參數

*目的地*<br/>
[out]作業的目的地。

*Data*<br/>
[in]要儲存的資料。

*計數*<br/>
[in]要寫入的雙字組的區塊的長度。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__stosd`|x86、x64|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

結果是 doubleword`Data`寫入至區塊`Count`所指向的記憶體位置的雙字組`Dest`。

此常式僅可作為內建常式使用。

## <a name="example"></a>範例

```
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

[編譯器內建](../intrinsics/compiler-intrinsics.md)