---
title: __readdr
ms.date: 09/02/2019
f1_keywords:
- __readdr
helpviewer_keywords:
- __readdr intrinsic
ms.assetid: 061b05da-c85e-4052-b392-106f14bb84f1
ms.openlocfilehash: 646330ca92af08903485fd4583eb2c217fe3e023
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216683"
---
# <a name="__readdr"></a>__readdr

讀取指定之調試暫存器的值。

## <a name="syntax"></a>語法

```C
unsigned         __readdr(unsigned int DebugRegister); /* x86 */
unsigned __int64 __readdr(unsigned int DebugRegister); /* x64 */
```

### <a name="parameters"></a>參數

*DebugRegister*\
在從0到7的常數, 識別 debug 暫存器。

## <a name="return-value"></a>傳回值

所指定 debug 暫存器的值。

## <a name="remarks"></a>備註

這些內建函式僅適用于核心模式, 而常式僅供內建函式使用。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__readdr`|x86、x64|

**標頭檔**\<intrin.h. h >

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)\
[__readeflags](../intrinsics/readeflags.md)
