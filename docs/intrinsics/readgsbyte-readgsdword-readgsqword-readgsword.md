---
title: __readgsbyte、__readgsdword、__readgsqword、__readgsword
ms.date: 11/04/2016
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
ms.openlocfilehash: fee7101ab72b9a0aecffb8ab8365dda1ec52d170
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220409"
---
# <a name="readgsbyte-readgsdword-readgsqword-readgsword"></a>__readgsbyte、__readgsdword、__readgsqword、__readgsword

**Microsoft 專屬**

讀取記憶體從相對於 GS 區段開頭的位移所指定的位置。

## <a name="syntax"></a>語法

```
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

#### <a name="parameters"></a>參數

*位移*<br/>
[in]從開頭的位移`GS`來讀取。

## <a name="return-value"></a>傳回值

記憶體中的位元組、 單字、 雙字組或 （如下所呼叫的函式的名稱） 的 quadword 內容位於位置`GS:[Offset]`。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__readgsbyte`|X64|
|`__readgsdword`|X64|
|`__readgsqword`|X64|
|`__readgsword`|X64|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

這些常式僅可作為內建。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[__writegsbyte、 \__writegsdword， \__writegsqword， \__writegsword](../intrinsics/writegsbyte-writegsdword-writegsqword-writegsword.md)<br/>
[編譯器內建](../intrinsics/compiler-intrinsics.md)
