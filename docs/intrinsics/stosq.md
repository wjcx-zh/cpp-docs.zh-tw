---
title: __stosq
ms.date: 11/04/2016
f1_keywords:
- __stosq
helpviewer_keywords:
- rep stosq instruction
- stosq instruction
- __stosq intrinsic
ms.assetid: 3ea28297-4369-4c2d-bf0c-91fa539ce209
ms.openlocfilehash: eacb12f7c02b82607d980281f8d4a0bc1e1d7c14
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59032429"
---
# <a name="stosq"></a>__stosq

**Microsoft 專屬**

產生的存放區的字串指示 (`rep stosq`)。

## <a name="syntax"></a>語法

```
void __stosb(
   unsigned __int64* Dest,
   unsigned __int64 Data,
   size_t Count
);
```

#### <a name="parameters"></a>參數

*目的地*<br/>
[out]作業的目的地。

*Data*<br/>
[in]要儲存的資料。

*計數*<br/>
[in]要寫入的 quadwords 區塊的長度。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__stosq`|AMD64|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

結果是 quadword`Data`寫入至區塊`Count`quadwords 中的`Dest`字串。

此常式僅可作為內建常式使用。

## <a name="example"></a>範例

```
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

## <a name="output"></a>Output

```
0 ffffffffffff ffffffffffff 0
```

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)