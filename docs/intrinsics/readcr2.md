---
title: __readcr2
ms.date: 09/02/2019
f1_keywords:
- __readcr2
helpviewer_keywords:
- __readcr2 intrinsic
ms.assetid: d02c97d8-1953-46e7-a79e-a781e2c5bf27
ms.openlocfilehash: 482f4548a692d6aa3b65fbc42caabda29bb393c1
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217101"
---
# <a name="__readcr2"></a>__readcr2

**Microsoft 專屬**

讀取 CR2 暫存器, 並傳回其值。

## <a name="syntax"></a>語法

```C
unsigned __int64 __readcr2(void);
```

## <a name="return-value"></a>傳回值

CR2 暫存器中的值。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__readcr2`|x86、x64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

內建函式僅適用于核心模式, 而常式僅以內建函式的形式提供。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
