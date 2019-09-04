---
title: __incfsbyte、__incfsword、__incfsdword
ms.date: 09/02/2019
f1_keywords:
- __incfsword
- __incfsbyte_cpp
- __incfsbyte
- __incfsdword
- __incfsword_cpp
- __incfsdword_cpp
helpviewer_keywords:
- __incfsword intrinsic
- __incfsdword intrinsic
- __incfsbyte intrinsic
ms.assetid: 820457fb-e35e-42d3-bcb6-725da3281c64
ms.openlocfilehash: 43824829043304f5762d049b5c75a72b57e2102c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222134"
---
# <a name="__incfsbyte-__incfsword-__incfsdword"></a>__incfsbyte、__incfsword、__incfsdword

**Microsoft 專屬**

在相對於`FS`區段開頭的位移所指定的記憶體位置, 將一個值加一。

## <a name="syntax"></a>語法

```C
void __incfsbyte(
   unsigned long Offset
);
void __incfsword(
   unsigned long Offset
);
void __incfsdword(
   unsigned long Offset
);
```

### <a name="parameters"></a>參數

*投影*\
在從開頭算起`FS`的位移。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__incfsbyte`|x86|
|`__incfsword`|x86|
|`__incfsdword`|x86|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

這些內建函式僅適用于核心模式, 而常式僅供內建函式使用。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[\__addfsbyte、 \__addfsword、 \__addfsdword](../intrinsics/addfsbyte-addfsword-addfsdword.md)\
[\__readfsbyte、 \__readfsdword、 \__readfsqword、 \__readfsword](../intrinsics/readfsbyte-readfsdword-readfsqword-readfsword.md)\
[\__writefsbyte、 \__writefsdword、 \__writefsqword、 \__writefsword](../intrinsics/writefsbyte-writefsdword-writefsqword-writefsword.md)\
[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
