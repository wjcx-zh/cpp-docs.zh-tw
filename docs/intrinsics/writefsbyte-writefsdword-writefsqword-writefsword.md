---
title: __writefsbyte、__writefsdword、__writefsqword、__writefsword
ms.date: 09/02/2019
f1_keywords:
- __writefsword
- __writefsbyte
- __writefsqword
- __writefsdword
helpviewer_keywords:
- writefsbyte intrinsic
- __writefsword intrinsic
- writefsqword intrinsic
- writefsdword intrinsic
- __writefsdword intrinsic
- __writefsqword intrinsic
- __writefsbyte intrinsic
- writefsword intrinsic
ms.assetid: 23ac6e8e-bc91-4e90-a4c6-da02993637ad
ms.openlocfilehash: c0cb70986fc75d14f23fb70efe89f48e10fb047e
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219122"
---
# <a name="__writefsbyte-__writefsdword-__writefsqword-__writefsword"></a>__writefsbyte、__writefsdword、__writefsqword、__writefsword

**Microsoft 專屬**

將記憶體寫入相對於 FS 區段開頭之位移所指定的位置。

## <a name="syntax"></a>語法

```C
void __writefsbyte(
   unsigned long Offset,
   unsigned char Data
);
void __writefsword(
   unsigned long Offset,
   unsigned short Data
);
void __writefsdword(
   unsigned long Offset,
   unsigned long Data
);
void __writefsqword(
   unsigned long Offset,
   unsigned __int64 Data
);
```

### <a name="parameters"></a>參數

*投影*\
在從 FS 開頭到寫入的位移。

*Data*\
在要寫入的值。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__writefsbyte`|x86|
|`__writefsword`|x86|
|`__writefsdword`|x86|
|`__writefsqword`|x86|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

這些常式僅供內建函式使用。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[__readfsbyte、 \__readfsdword、 \__readfsqword、 \__readfsword](../intrinsics/readfsbyte-readfsdword-readfsqword-readfsword.md)\
[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
