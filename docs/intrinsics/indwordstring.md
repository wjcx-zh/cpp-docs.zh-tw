---
title: __indwordstring
ms.date: 09/02/2019
f1_keywords:
- __indwordstring
- __indwordstring_cpp
helpviewer_keywords:
- __indwordstring intrinsic
- rep insd instruction
ms.assetid: 96a1cf33-f691-4916-99e4-fa849b61e3a9
ms.openlocfilehash: b0b160ba00b1c0b7aa6bffc913e4cb56d503c2ff
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217830"
---
# <a name="__indwordstring"></a>__indwordstring

**Microsoft 專屬**

使用`rep insd`指令, 從指定的埠讀取資料。

## <a name="syntax"></a>語法

```C
void __indwordstring(
   unsigned short Port,
   unsigned long* Buffer,
   unsigned long Count
);
```

### <a name="parameters"></a>參數

*移植*\
在要從中讀取的埠。

*緩衝區*\
脫銷從埠讀取的資料會在此寫入。

*計數*\
在要讀取的資料位元組數目。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__indwordstring`|x86、x64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

此常式僅可作為內建常式使用。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
