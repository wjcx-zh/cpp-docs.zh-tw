---
title: __writegsbyte、__writegsdword、__writegsqword、__writegsword
ms.date: 11/04/2016
f1_keywords:
- __writegsbyte
- __writegsqword
- __writegsdword
- __writegsword
helpviewer_keywords:
- __writegsqword intrinsic
- __writegsbyte intrinsic
- __writegsword intrinsic
- __writegsdword intrinsic
ms.assetid: 7746cf6d-2259-4139-9aab-c07dd75c8037
ms.openlocfilehash: dbd3fff75107ae61f7680dee84b72ff3153bfa8e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389771"
---
# <a name="writegsbyte-writegsdword-writegsqword-writegsword"></a>__writegsbyte、__writegsdword、__writegsqword、__writegsword

**Microsoft 專屬**

寫入記憶體相對於 GS 區段開頭的位移所指定的位置。

## <a name="syntax"></a>語法

```
void __writegsbyte(
   unsigned long Offset,
   unsigned char Data
);
void __writegsword(
   unsigned long Offset,
   unsigned short Data
);
void __writegsdword(
   unsigned long Offset,
   unsigned long Data
);
void __writegsqword(
   unsigned long Offset,
   unsigned __int64 Data
);
```

#### <a name="parameters"></a>參數

*Offset*<br/>
[in]從要寫入的 GS 開頭的位移。

*Data*<br/>
[in]要寫入的值。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__writegsbyte`|X64|
|`__writegsdword`|X64|
|`__writegsqword`|X64|
|`__writegsword`|X64|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

這些常式僅可作為內建。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[__readgsbyte、 \__readgsdword， \__readgsqword， \__readgsword](../intrinsics/readgsbyte-readgsdword-readgsqword-readgsword.md)<br/>
[編譯器內建](../intrinsics/compiler-intrinsics.md)
