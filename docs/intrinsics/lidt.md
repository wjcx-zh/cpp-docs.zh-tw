---
title: __lidt
ms.date: 11/04/2016
f1_keywords:
- __lidt
- __lidt_cpp
helpviewer_keywords:
- LIDT instruction
- __lidt intrinsic
ms.assetid: 8298d25d-a19e-4900-828d-6b3b09841882
ms.openlocfilehash: 757309603af48820a17668cfe272bbeaad9239b3
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59038469"
---
# <a name="lidt"></a>__lidt

**Microsoft 特定的**

載入中斷描述項表登錄 (IDTR) 中指定的記憶體位置的值。

## <a name="syntax"></a>語法

```
void __lidt(void * Source);
```

#### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*原始程式檔*|[in]要複製到 IDTR 值指標。|

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__lidt`|x86、x64|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

`__lidt`函式相當於`LIDT`機器指令，且只適用於核心模式。 如需詳細資訊，搜尋文件中，「 Intel 架構軟體開發人員的手動、 磁碟區 2:指令集參考，「 在[Intel Corporation](https://software.intel.com/articles/intel-sdm)站台。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)<br/>
[__sidt](../intrinsics/sidt.md)