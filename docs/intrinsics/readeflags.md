---
title: __readeflags
ms.date: 09/02/2019
f1_keywords:
- __readeflags
helpviewer_keywords:
- __readeflags intrinsic
ms.assetid: f9d2f4d8-c428-491f-b8de-04d0566b2b6b
ms.openlocfilehash: 6afdc0f20a3ae72865a80ba2eb7f896f79f63171
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857901"
---
# <a name="__readeflags"></a>__readeflags

**Microsoft 專屬**

讀取程式狀態和控制（EFLAGS）註冊。

## <a name="syntax"></a>語法

```C
unsigned     int __readeflags(void); /* x86 */
unsigned __int64 __readeflags(void); /* x64 */
```

## <a name="return-value"></a>傳回值

EFLAGS 註冊的值。 在32位平臺上，傳回值為32位長，而在64位平臺上則為64位長。

## <a name="remarks"></a>備註

這些常式僅供內建函式使用。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__readeflags`|x86、x64|

**標頭檔**\<intrin.h >

**結束 Microsoft 專屬**

## <a name="see-also"></a>請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)\
[__writeeflags](../intrinsics/writeeflags.md)
