---
title: __inword
ms.date: 09/02/2019
f1_keywords:
- __indword_cpp
- __indword
helpviewer_keywords:
- in instruction
- __inword intrinsic
ms.assetid: 5c617edd-6709-40a1-aad2-40d5e39283c6
ms.openlocfilehash: cfb6e5a11bed5feec3435ab604d22b8f532d3400
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217523"
---
# <a name="__inword"></a>__inword

**Microsoft 專屬**

使用`in`指令, 從指定的埠讀取資料。

## <a name="syntax"></a>語法

```C
unsigned short __inword(
   unsigned short Port
);
```

### <a name="parameters"></a>參數

*移植*\
在要從中讀取的埠。

## <a name="return-value"></a>傳回值

讀取的資料字。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__inword`|x86、x64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

此常式僅可作為內建常式使用。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
