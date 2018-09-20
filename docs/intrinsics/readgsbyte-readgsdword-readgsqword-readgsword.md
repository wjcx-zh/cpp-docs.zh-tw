---
title: __readgsbyte、 __readgsdword、 __readgsqword、 __readgsword |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __readgsbyte
- __readgsdword
- __readgsqword
- __readgsword
dev_langs:
- C++
helpviewer_keywords:
- __readgsword intrinsic
- __readgsdword intrinsic
- __readgsqword intrinsic
- __readgsbyte intrinsic
ms.assetid: f822632d-854c-4558-a71b-cdfc3eea2236
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8afe4d646e77e87c1c679d8b7e3bd09679c7b16d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46414546"
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

這些內建函式僅適用於核心模式，常式僅可作為內建函式。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[__writegsbyte、 \__writegsdword， \__writegsqword， \__writegsword](../intrinsics/writegsbyte-writegsdword-writegsqword-writegsword.md)<br/>
[編譯器內建](../intrinsics/compiler-intrinsics.md)