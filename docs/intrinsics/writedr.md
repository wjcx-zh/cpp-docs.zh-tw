---
title: __writedr
ms.date: 09/02/2019
f1_keywords:
- __writedr
helpviewer_keywords:
- __writedr intrinsic
ms.assetid: ac55c1ee-df2f-41d4-a429-6f369d2a934d
ms.openlocfilehash: 715ef7432d506c2758c9c3da913e9c0ebb24e13f
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219231"
---
# <a name="__writedr"></a>__writedr

將指定的值寫入指定的 debug 暫存器。

## <a name="syntax"></a>語法

```C
void __writedr(unsigned DebugRegister, unsigned DebugValue); /* x86 */
void __writedr(unsigned DebugRegister, unsigned __int64 DebugValue); /* x64 */
```

### <a name="parameters"></a>參數

*DebugRegister*\
在從0到7的數位, 用來識別 debug 暫存器。

*DebugValue*\
在要寫入 debug 暫存器的值。

## <a name="remarks"></a>備註

這些內建函式僅適用于核心模式, 而常式僅供內建函式使用。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__writedr`|x86、x64|

**標頭檔**\<intrin.h. h >

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)\
[__readdr](../intrinsics/readdr.md)
