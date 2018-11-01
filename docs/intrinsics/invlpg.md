---
title: __invlpg
ms.date: 11/04/2016
f1_keywords:
- __invlpg
- __invlpg_cpp
helpviewer_keywords:
- invlpg instruction
- __invlpg intrinsic
ms.assetid: 3fb3633f-d9b7-4ec0-9e7f-a7f2fa8ed794
ms.openlocfilehash: 0ff46aa15fbb8728ce02255209a32f01a168609b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50629381"
---
# <a name="invlpg"></a>__invlpg

**Microsoft 專屬**

會產生 x86`invlpg`失效轉譯對應緩衝區 (TLB) 頁面所指向的記憶體與相關聯的指令`Address`。

## <a name="syntax"></a>語法

```
void __invlpg(
   void* Address
);
```

#### <a name="parameters"></a>參數

*地址*<br/>
[in]64 位元的位址。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__invlpg`|x86、x64|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

此內建`__invlpg`發出特殊權限的指令，僅適用於核心模式特殊權限層級 (CPL) 為 0。

此常式僅可作為內建常式使用。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)