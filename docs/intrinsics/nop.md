---
title: __nop
ms.date: 09/02/2019
f1_keywords:
- __nop
helpviewer_keywords:
- nop instruction
- __nop intrinsic
ms.assetid: 7a2a938b-87e0-476d-a348-03ea7635b6b9
ms.openlocfilehash: 4561bcb84063f3707825c8ca164867d41500e2db
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221667"
---
# <a name="__nop"></a>__nop

**Microsoft 專屬**

產生不執行任何作業的平臺特定機器程式碼。

## <a name="syntax"></a>語法

```C
void __nop();
```

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__nop`|x86、ARM、x64、ARM64|

**標頭檔**\<intrin.h. h >

**結束 Microsoft 專屬**

## <a name="remarks"></a>備註

`__nop` 函式相當於 `NOP` 機器指令。 如需 x86 和 x64 的詳細資訊, 請搜尋檔「Intel 架構軟體發展人員手冊, 第2卷:指示集參考, 位於[Intel Corporation](https://software.intel.com/articles/intel-sdm)網站。

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)\
[__noop](../intrinsics/noop.md)
