---
title: __invlpg
ms.date: 09/02/2019
f1_keywords:
- __invlpg
- __invlpg_cpp
helpviewer_keywords:
- invlpg instruction
- __invlpg intrinsic
ms.assetid: 3fb3633f-d9b7-4ec0-9e7f-a7f2fa8ed794
ms.openlocfilehash: ba8bd81498f805992336b0dc4163fe18fa157a2c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221891"
---
# <a name="__invlpg"></a>__invlpg

**Microsoft 專屬**

產生 x86 `invlpg`指令, 使與*位址*所指向之記憶體相關聯的頁面轉譯對應緩衝區 (TLB) 失效。

## <a name="syntax"></a>語法

```C
void __invlpg(
   void* Address
);
```

### <a name="parameters"></a>參數

*應對*\
在64位位址。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__invlpg`|x86、x64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

內建會發出特殊許可權指令, 而且只有在具有許可權層級 (CPL) 為0的核心模式下才可使用。 `__invlpg`

此常式僅可作為內建常式使用。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
