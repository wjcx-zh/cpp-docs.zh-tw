---
title: __readcr3
ms.date: 09/02/2019
f1_keywords:
- __readcr3
helpviewer_keywords:
- __readcr3 intrinsic
ms.assetid: e24392c3-cad7-4788-8f31-94bf2e9e0053
ms.openlocfilehash: b03ff46fabc99839d9c0bbd5c72e1b76d25814c0
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221273"
---
# <a name="__readcr3"></a>__readcr3

**Microsoft 專屬**

讀取 CR3 暫存器, 並傳回其值。

## <a name="syntax"></a>語法

```C
unsigned __int64 __readcr3(void);
```

## <a name="return-value"></a>傳回值

CR3 暫存器中的值。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__readcr3`|x86、x64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

內建函式僅適用于核心模式, 而常式僅以內建函式的形式提供。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
