---
title: __movsq
ms.date: 11/04/2016
f1_keywords:
- __movsq
helpviewer_keywords:
- __movsq intrinsic
- rep movsq instruction
- movsq instruction
ms.assetid: be116a6e-2176-4ca4-93b1-9ccf3e7e7835
ms.openlocfilehash: 06f42befa24d4024b3ad4b0c0a8d0897cb2aee9b
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51326364"
---
# <a name="movsq"></a>__movsq

**Microsoft 專屬**

會產生重複的移動字串 (`rep movsq`) 指令。

## <a name="syntax"></a>語法

```
void __movsq(
   unsigned char* Dest,
   unsigned char* Source,
   size_t Count
);
```

#### <a name="parameters"></a>參數

*目的地*<br/>
[out]作業的目的地。

*來源*<br/>
[in]作業的來源。

*計數*<br/>
[in]若要複製的 quadwords 數目。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__movsq`|X64|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

結果是第一個`Count`所指向 quadwords`Source`複製到`Dest`字串。

此常式僅可作為內建常式使用。

## <a name="example"></a>範例

```
// movsq.cpp
// processor: x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__movsq)

int main()
{
    unsigned __int64 a1[10];
    unsigned __int64 a2[10] = {950, 850, 750, 650, 550, 450, 350, 250,
                               150, 50};
    __movsq(a1, a2, 10);

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