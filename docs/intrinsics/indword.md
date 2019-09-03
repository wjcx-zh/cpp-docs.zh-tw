---
title: __indword
ms.date: 09/02/2019
f1_keywords:
- __indword_cpp
- __indword
helpviewer_keywords:
- in instruction
- __indword intrinsic
ms.assetid: 1068d686-586e-4e36-b962-d1d7c3315260
ms.openlocfilehash: 790b65c8a565124df92b82b7ea17174788086a96
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222113"
---
# <a name="__indword"></a>__indword

**Microsoft 專屬**

使用`in`指令, 從指定的埠讀取一個雙單字的資料。

## <a name="syntax"></a>語法

```C
unsigned long __indword(
   unsigned short Port
);
```

### <a name="parameters"></a>參數

*移植*\
在要從中讀取的埠。

## <a name="return-value"></a>傳回值

從埠讀取的文字。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__indword`|x86、x64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

此常式僅可作為內建常式使用。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
