---
title: __wbinvd
ms.date: 09/02/2019
f1_keywords:
- __wbinvd
helpviewer_keywords:
- __wbinvd intrinsic
- wbinvd instruction
ms.assetid: 628d0981-39e5-49e1-bd43-706d123af121
ms.openlocfilehash: fe888ef578f0c2e077911537d401890b63372a0b
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219379"
---
# <a name="__wbinvd"></a>__wbinvd

**Microsoft 專屬**

產生回寫並使 Cache (`wbinvd`) 指令失效。

## <a name="syntax"></a>語法

```C
void __wbinvd(void);
```

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__wbinvd`|x86、x64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

此函式僅適用于具有許可權層級 (CPL) 為0的核心模式, 而常式僅以內建函式的形式提供。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
