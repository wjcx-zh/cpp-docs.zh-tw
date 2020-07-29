---
title: __readmsr
ms.date: 09/02/2019
f1_keywords:
- __readmsr
helpviewer_keywords:
- Read Model Specific Register
- rdmsr instruction
- __readmsr intrinsic
ms.assetid: 7ab1f8e8-72cb-4ce4-817d-3e728a3c9716
ms.openlocfilehash: 029119bc47d0172c7e9cc5fbf8cd20c4ee23e0f0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219647"
---
# <a name="__readmsr"></a>__readmsr

**Microsoft 特定的**

產生 `rdmsr` 指令，其會讀取所指定的模型特定暫存器 **`register`** ，並傳回其值。

## <a name="syntax"></a>語法

```C
__int64 __readmsr(
   int register
);
```

### <a name="parameters"></a>參數

*參加*\
在要讀取的模型特定暫存器。

## <a name="return-value"></a>傳回值

指定之暫存器中的值。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__readmsr`|x86、x64|

**標頭檔** \<intrin.h>

## <a name="remarks"></a>備註

此函式僅適用于核心模式，而常式僅以內建函式的形式提供。

如需詳細資訊，請參閱 AMD 檔。

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
