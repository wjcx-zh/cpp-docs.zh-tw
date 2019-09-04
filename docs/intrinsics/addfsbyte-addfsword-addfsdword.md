---
title: __addfsbyte、__addfsword、__addfsdword
ms.date: 09/02/2019
f1_keywords:
- __addfsbyte_cpp
- __addfsdword
- __addfsword_cpp
- __addfsbyte
- __addfsword
- __addfsdword_cpp
helpviewer_keywords:
- __addfsdword intrinsic
- __addfsword intrinsic
- __addfsbyte intrinsic
ms.assetid: 706c70df-6b52-4401-9268-2977ed8ad715
ms.openlocfilehash: 302e58ed13c144913e7806a0a8b7adc202a67ef6
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218518"
---
# <a name="__addfsbyte-__addfsword-__addfsdword"></a>__addfsbyte、__addfsword、__addfsdword

**Microsoft 專屬**

將值新增至相對於`FS`區段開頭之位移所指定的記憶體位置。

## <a name="syntax"></a>語法

```C
void __addfsbyte(
   unsigned long Offset,
   unsigned char Data
);
void __addfsword(
   unsigned long Offset,
   unsigned short Data
);
void __addfsdword(
   unsigned long Offset,
   unsigned long Data
);
```

### <a name="parameters"></a>參數

*投影*\
在從開頭算起`FS`的位移。

*Data*\
在要加入至記憶體位置的值。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__addfsbyte`|x86|
|`__addfsword`|x86|
|`__addfsdword`|x86|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

這些常式僅供內建函式使用。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[__incfsbyte、 \__incfsword、 \__incfsdword](../intrinsics/incfsbyte-incfsword-incfsdword.md)\
[__readfsbyte、 \__readfsdword、 \__readfsqword、 \__readfsword](../intrinsics/readfsbyte-readfsdword-readfsqword-readfsword.md)\
[__writefsbyte、 \__writefsdword、 \__writefsqword、 \__writefsword](../intrinsics/writefsbyte-writefsdword-writefsqword-writefsword.md)\
[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
