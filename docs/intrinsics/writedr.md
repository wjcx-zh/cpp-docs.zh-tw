---
title: __writedr
ms.date: 11/04/2016
f1_keywords:
- __writedr
helpviewer_keywords:
- __writedr intrinsic
ms.assetid: ac55c1ee-df2f-41d4-a429-6f369d2a934d
ms.openlocfilehash: f8049485d40185d83ed01c91ad336e83f3e79834
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651811"
---
# <a name="writedr"></a>__writedr

將指定的值寫入至指定的偵錯器。

## <a name="syntax"></a>語法

```
void __writedr(unsigned DebugRegister, unsigned DebugValue);
void __writedr(unsigned DebugRegister, unsigned __int64 DebugValue);
```

#### <a name="parameters"></a>參數

*DebugRegister*<br/>
[in]從 0 到 7 可識別偵錯的數字註冊。

*DebugValue*<br/>
[in]要寫入至偵錯值暫存器。

## <a name="remarks"></a>備註

這些內建函式是只適用於核心模式，而只提供內建函式常式。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__writedr`|x86、x64|

**標頭檔** \<intrin.h >

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)<br/>
[__readdr](../intrinsics/readdr.md)