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
ms.openlocfilehash: 4398b9d42369e3a914dbec1ed2d14cafecf58483
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222334"
---
# <a name="__readmsr"></a>__readmsr

**Microsoft 專屬**

產生指令, 其會讀取所`register`指定的模型特定暫存器, 並傳回其值。 `rdmsr`

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

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

此函式僅適用于核心模式, 而常式僅以內建函式的形式提供。

如需詳細資訊, 請參閱 AMD 檔。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
