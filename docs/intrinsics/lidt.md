---
title: __lidt
ms.date: 09/02/2019
f1_keywords:
- __lidt
- __lidt_cpp
helpviewer_keywords:
- LIDT instruction
- __lidt intrinsic
ms.assetid: 8298d25d-a19e-4900-828d-6b3b09841882
ms.openlocfilehash: 87a49643e7cd11ae57dc01130f250895cf012065
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88562489"
---
# <a name="__lidt"></a>__lidt

**Microsoft 特定的**

使用指定記憶體位置中的值，載入中斷描述項資料表 (IDTR) 。

## <a name="syntax"></a>語法

```C
void __lidt(void * Source);
```

### <a name="parameters"></a>參數

*源*\
在要複製到 IDTR 的值指標。

## <a name="requirements"></a>規格需求

|內建|架構|
|---------------|------------------|
|`__lidt`|x86、x64|

**標頭檔** \<intrin.h>

## <a name="remarks"></a>備註

函式 `__lidt` 相當於 `LIDT` 電腦指令，而且只能在核心模式中使用。 如需詳細資訊，請在 [Intel Corporation](https://software.intel.com/articles/intel-sdm) 網站搜尋「Intel 架構軟體發展人員手冊，第2卷：指令集參考」檔。

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)\
[__sidt](../intrinsics/sidt.md)
