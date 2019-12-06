---
title: __readdr
ms.date: 09/02/2019
f1_keywords:
- __readdr
helpviewer_keywords:
- __readdr intrinsic
ms.assetid: 061b05da-c85e-4052-b392-106f14bb84f1
ms.openlocfilehash: fbaf9e761f9f1450ccd12dc378ab6e498aa0df08
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857875"
---
# <a name="__readdr"></a>__readdr

**Microsoft 專屬**

讀取指定之調試暫存器的值。

## <a name="syntax"></a>語法

```C
unsigned         __readdr(unsigned int DebugRegister); /* x86 */
unsigned __int64 __readdr(unsigned int DebugRegister); /* x64 */
```

### <a name="parameters"></a>參數

*DebugRegister*\
在從0到7的常數，識別 debug 暫存器。

## <a name="return-value"></a>傳回值

所指定 debug 暫存器的值。

## <a name="remarks"></a>備註

這些內建函式僅適用于核心模式，而常式僅供內建函式使用。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__readdr`|x86、x64|

**標頭檔**\<intrin.h >

**結束 Microsoft 專屬**

## <a name="see-also"></a>請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)\
[__readeflags](../intrinsics/readeflags.md)
