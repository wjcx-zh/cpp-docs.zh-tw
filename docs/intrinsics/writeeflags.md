---
title: __writeeflags
ms.date: 09/02/2019
f1_keywords:
- __writeeflags
helpviewer_keywords:
- __writeeflags intrinsics
ms.assetid: a62a522c-d7fa-4f10-a620-a3b32bdf3f17
ms.openlocfilehash: 6b9b6976369ed810789e5749a2e30029cad4c2d7
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74858044"
---
# <a name="__writeeflags"></a>__writeeflags

**Microsoft 專屬**

將指定的值寫入至程式狀態和控制（EFLAGS）暫存器。

## <a name="syntax"></a>語法

```C
void __writeeflags(unsigned Value); /* x86 */
void __writeeflags(unsigned __int64 Value); /* x64 */
```

### <a name="parameters"></a>參數

*Value*\
在要寫入 EFLAGS 暫存器的值。 32位平臺的 `Value` 參數是32位長，而64位平臺則為64位長。

## <a name="remarks"></a>備註

這些常式僅供內建函式使用。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__writeeflags`|x86、x64|

**標頭檔**\<intrin.h >

**結束 Microsoft 專屬**

## <a name="see-also"></a>請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)\
[__readeflags](../intrinsics/readeflags.md)
