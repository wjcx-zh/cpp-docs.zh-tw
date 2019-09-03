---
title: __writecr4
ms.date: 09/02/2019
f1_keywords:
- _writecr4
helpviewer_keywords:
- _writecr4 intrinsic
ms.assetid: ab7651d7-b86b-4be7-a0a0-7263099c70fc
ms.openlocfilehash: 1afdadcdfdbf1060c87e3865dd5597b0b9a2ea6b
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219264"
---
# <a name="__writecr4"></a>__writecr4

**Microsoft 專屬**

將值`Data`寫入 CR4 暫存器。

## <a name="syntax"></a>語法

```C
void writecr4(
   unsigned __int64 Data
);
```

### <a name="parameters"></a>參數

*Data*\
在要寫入 CR4 暫存器的值。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__writecr4`|x86、x64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

此內建只適用於核心模式，且此常式僅可作為內建常式使用。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
