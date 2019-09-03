---
title: __writecr3
ms.date: 09/02/2019
f1_keywords:
- _writecr3
helpviewer_keywords:
- _writecr3 intrinsic
ms.assetid: 959d49fa-69d5-47cf-88d2-7688367fe38f
ms.openlocfilehash: f2472a21fe42f10dbf0918480ef02f7e48109747
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219285"
---
# <a name="__writecr3"></a>__writecr3

**Microsoft 專屬**

將值`Data`寫入 CR3 暫存器。

## <a name="syntax"></a>語法

```C
void writecr3(
   unsigned __int64 Data
);
```

### <a name="parameters"></a>參數

*Data*\
在要寫入 CR3 暫存器的值。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__writecr3`|x86、x64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

此內建只適用於核心模式，且此常式僅可作為內建常式使用。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
