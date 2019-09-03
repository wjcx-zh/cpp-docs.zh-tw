---
title: __readgsbyte、__readgsdword、__readgsqword、__readgsword
ms.date: 09/02/2019
f1_keywords:
- __readgsbyte
- __readgsdword
- __readgsqword
- __readgsword
helpviewer_keywords:
- __readgsword intrinsic
- __readgsdword intrinsic
- __readgsqword intrinsic
- __readgsbyte intrinsic
ms.assetid: f822632d-854c-4558-a71b-cdfc3eea2236
ms.openlocfilehash: 278f1de33a7e01c5893217ddd8aaa22e68cf0c94
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222357"
---
# <a name="__readgsbyte-__readgsdword-__readgsqword-__readgsword"></a>__readgsbyte、__readgsdword、__readgsqword、__readgsword

**Microsoft 專屬**

從相對於 GS 區段開頭的位移所指定的位置讀取記憶體。

## <a name="syntax"></a>語法

```C
unsigned char __readgsbyte(
   unsigned long Offset
);
unsigned short __readgsword(
   unsigned long Offset
);
unsigned long __readgsdword(
   unsigned long Offset
);
unsigned __int64 __readgsqword(
   unsigned long Offset
);
```

### <a name="parameters"></a>參數

*投影*\
在從開始`GS`讀取的位移。

## <a name="return-value"></a>傳回值

位在位置`GS:[Offset]`的位元組、單字、雙單字或四字的記憶體內容 (如所呼叫的函式名稱所示)。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__readgsbyte`|X64|
|`__readgsdword`|X64|
|`__readgsqword`|X64|
|`__readgsword`|X64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

這些常式僅以內建函式的形式提供。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[__writegsbyte、 \__writegsdword、 \__writegsqword、 \__writegsword](../intrinsics/writegsbyte-writegsdword-writegsqword-writegsword.md)\
[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
