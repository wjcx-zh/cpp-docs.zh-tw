---
title: __inbytestring
ms.date: 09/02/2019
f1_keywords:
- __inbytestring
- __inbytestring_cpp
helpviewer_keywords:
- rep insb instruction
- __inbytestring intrinsic
ms.assetid: fe549556-e7a3-4af3-8ebf-8a7dc3cb233b
ms.openlocfilehash: cb6e811c809c6069c47415e87804641f30a3897b
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217807"
---
# <a name="__inbytestring"></a>__inbytestring

**Microsoft 專屬**

使用`rep insb`指令, 從指定的埠讀取資料。

## <a name="syntax"></a>語法

```C
void __inbytestring(
   unsigned short Port,
   unsigned char* Buffer,
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
|`__inbytestring`|x86、x64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

此常式僅可作為內建常式使用。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
