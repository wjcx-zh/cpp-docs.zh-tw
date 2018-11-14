---
title: __writefsbyte、__writefsdword、__writefsqword、__writefsword
ms.date: 11/04/2016
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
ms.openlocfilehash: 26322b210105f694be764418d9e0b77a0d419844
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51328483"
---
# <a name="writefsbyte-writefsdword-writefsqword-writefsword"></a>__writefsbyte、__writefsdword、__writefsqword、__writefsword

**Microsoft 專屬**

寫入記憶體相對於 FS 區段開頭的位移所指定的位置。

## <a name="syntax"></a>語法

```
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

#### <a name="parameters"></a>參數

*位移*<br/>
[in]從要寫入的 FS 開頭的位移。

*Data*<br/>
[in]要寫入的值。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__writefsbyte`|x86|
|`__writefsword`|x86|
|`__writefsdword`|x86|
|`__writefsqword`|x86|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

這些常式都僅有內建函式。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[__readfsbyte、 \__readfsdword， \__readfsqword， \__readfsword](../intrinsics/readfsbyte-readfsdword-readfsqword-readfsword.md)<br/>
[編譯器內建](../intrinsics/compiler-intrinsics.md)