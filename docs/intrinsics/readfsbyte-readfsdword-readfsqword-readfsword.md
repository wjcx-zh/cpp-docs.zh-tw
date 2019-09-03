---
title: __readfsbyte、__readfsdword、__readfsqword、__readfsword
ms.date: 09/02/2019
f1_keywords:
- __readfsword
- __readfsdword
- __readfsbyte
- __readfsqword
helpviewer_keywords:
- __readfsword intrinsic
- readfsword intrinsic
- __readfsdword intrinsic
- readfsbyte intrinsic
- __readfsbyte intrinsic
- readfsdword intrinsic
- readfsqword intrinsic
- __readfsqword intrinsic
ms.assetid: f6ee7203-4179-402c-a464-0746c84ce6ac
ms.openlocfilehash: 30040b33fe8c686bc0cda585c525ae2926cdf314
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222371"
---
# <a name="__readfsbyte-__readfsdword-__readfsqword-__readfsword"></a>__readfsbyte、__readfsdword、__readfsqword、__readfsword

**Microsoft 專屬**

從相對於 FS 區段開頭的位移所指定的位置讀取記憶體。

## <a name="syntax"></a>語法

```C
unsigned char __readfsbyte(
   unsigned long Offset
);
unsigned short __readfsword(
   unsigned long Offset
);
unsigned long __readfsdword(
   unsigned long Offset
);
unsigned __int64 __readfsqword(
   unsigned long Offset
);
```

### <a name="parameters"></a>參數

*投影*\
在從開始`FS`讀取的位移。

## <a name="return-value"></a>傳回值

位在位置`FS:[Offset]`的位元組、字組、雙字或四字的記憶體內容 (如所呼叫的函式名稱所示)。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__readfsbyte`|x86|
|`__readfsdword`|x86|
|`__readfsqword`|x86|
|`__readfsword`|x86|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

這些常式僅供內建函式使用。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[__writefsbyte、 \__writefsdword、 \__writefsqword、 \__writefsword](../intrinsics/writefsbyte-writefsdword-writefsqword-writefsword.md)\
[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
