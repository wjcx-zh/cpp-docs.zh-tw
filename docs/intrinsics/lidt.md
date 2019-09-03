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
ms.openlocfilehash: 24778b761ada56830b155a2fc65e90f54ba729ed
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217516"
---
# <a name="__lidt"></a>__lidt

**Microsoft 專屬**

使用指定記憶體位置中的值, 載入中斷描述項資料表 register (IDTR)。

## <a name="syntax"></a>語法

```C
void __lidt(void * Source);
```

### <a name="parameters"></a>參數

|參數|說明|
|---------------|-----------------|
|*Source*|在要複製到 IDTR 的值指標。|

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__lidt`|x86、x64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

函式相當`LIDT`于機器指令, 而且只能在核心模式中使用。 `__lidt` 如需詳細資訊, 請搜尋檔「Intel 架構軟體發展人員手冊, 第2卷:指示集參考, 位於[Intel Corporation](https://software.intel.com/articles/intel-sdm)網站。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)\
[__sidt](../intrinsics/sidt.md)
