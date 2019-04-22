---
title: __movsb
ms.date: 11/04/2016
f1_keywords:
- __movsb
helpviewer_keywords:
- movsb instruction
- rep movsb instruction
- __movsb intrinsic
ms.assetid: ba5469f6-f797-4cd2-bee8-74c7666c26d4
ms.openlocfilehash: 42124743c27b297c723780c1bc19038fb54e638d
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59024990"
---
# <a name="movsb"></a>__movsb

**Microsoft 專屬**

產生的移動的字串 (`rep movsb`) 指令。

## <a name="syntax"></a>語法

```
void __movsb(
   unsigned char* Destination,
   unsigned const char* Source,
   size_t Count
);
```

#### <a name="parameters"></a>參數

*目的地*<br/>
[out]若要複製的目的地的指標。

*來源*<br/>
[in]要複製的來源指標。

*計數*<br/>
[in]要複製的位元組數目。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__movsb`|x86、x64|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

結果是第一個`Count`所指向的位元組`Source`複製到`Destination`字串。

此常式僅可作為內建常式使用。

## <a name="example"></a>範例

```
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

[編譯器內建](../intrinsics/compiler-intrinsics.md)