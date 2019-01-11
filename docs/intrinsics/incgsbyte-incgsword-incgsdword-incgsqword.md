---
title: __incgsbyte、__incgsword、__incgsdword、__incgsqword
ms.date: 11/04/2016
f1_keywords:
- __incgsdword
- __incgsqword_cpp
- __incgsword_cpp
- __incgsword
- __incgsbyte
- __incgsbyte_cpp
- __incgsqword
- __incgsdword_cpp
helpviewer_keywords:
- __incgsbyte intrinsic
- __incgsword intrinsic
- __incgsqword intrinsic
- __incgsdword intrinsic
ms.assetid: 06bfdf4f-7643-4fe0-8455-60ce3068073e
ms.openlocfilehash: c0fb12a56a8c6e0220818d54ee5ec7413fe56b43
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220253"
---
# <a name="incgsbyte-incgsword-incgsdword-incgsqword"></a>__incgsbyte、__incgsword、__incgsdword、__incgsqword

**Microsoft 專屬**

相對於開頭的位移所指定的記憶體位置中加入一個值`GS`區段。

## <a name="syntax"></a>語法

```
void __incgsbyte(
   unsigned long Offset
);
void __incgsword(
   unsigned long Offset
);
void __incgsdword(
   unsigned long Offset
);
void __incgsqword(
   unsigned long Offset
);
```

#### <a name="parameters"></a>參數

*位移*<br/>
[in]從開頭的位移`GS`。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__incgsbyte`|X64|
|`__incgsword`|X64|
|`__incgsdword`|X64|
|`__incgsqword`|X64|

## <a name="remarks"></a>備註

這些常式僅可作為內建。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[__addgsbyte、 \__addgsword， \__addgsdword， \__addgsqword](../intrinsics/addgsbyte-addgsword-addgsdword-addgsqword.md)<br/>
[__readgsbyte、 \__readgsdword， \__readgsqword， \__readgsword](../intrinsics/readgsbyte-readgsdword-readgsqword-readgsword.md)<br/>
[__writegsbyte、 \__writegsdword， \__writegsqword， \__writegsword](../intrinsics/writegsbyte-writegsdword-writegsqword-writegsword.md)<br/>
[編譯器內建](../intrinsics/compiler-intrinsics.md)
