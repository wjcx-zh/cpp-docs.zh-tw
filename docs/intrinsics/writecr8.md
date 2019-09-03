---
title: __writecr8
ms.date: 09/02/2019
f1_keywords:
- _writecr8
helpviewer_keywords:
- _writecr8 intrinsic
ms.assetid: 6f8bd632-dddb-4335-971e-1acee24aa2b9
ms.openlocfilehash: c8df13c15b5cd8a51b77d65ad930a1852809ee30
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219244"
---
# <a name="__writecr8"></a>__writecr8

**Microsoft 專屬**

將值`Data`寫入 CR8 暫存器。

## <a name="syntax"></a>語法

```C
void writecr8(
   unsigned __int64 Data
);
```

### <a name="parameters"></a>參數

*Data*\
在要寫入 CR8 暫存器的值。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__writecr8`|X64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

`__writecr8`內建函式僅適用于核心模式, 而常式僅以內建函式的形式提供。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
