---
title: __writegsbyte、 __writegsdword、 __writegsqword、 __writegsword |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __writegsbyte
- __writegsqword
- __writegsdword
- __writegsword
dev_langs:
- C++
helpviewer_keywords:
- __writegsqword intrinsic
- __writegsbyte intrinsic
- __writegsword intrinsic
- __writegsdword intrinsic
ms.assetid: 7746cf6d-2259-4139-9aab-c07dd75c8037
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8dded14f47c4c0305e4dc145ee2b006c76da9b8f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46393551"
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

*位移*<br/>
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

這些內建函式僅適用於核心模式，而這些常式僅可作為內建函式。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[__readgsbyte、 \__readgsdword， \__readgsqword， \__readgsword](../intrinsics/readgsbyte-readgsdword-readgsqword-readgsword.md)<br/>
[編譯器內建](../intrinsics/compiler-intrinsics.md)