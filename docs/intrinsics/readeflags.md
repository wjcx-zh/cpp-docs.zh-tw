---
title: __readeflags
ms.date: 09/02/2019
f1_keywords:
- __readeflags
helpviewer_keywords:
- __readeflags intrinsic
ms.assetid: f9d2f4d8-c428-491f-b8de-04d0566b2b6b
ms.openlocfilehash: fe2365c2837b6c583810bb9fc908fe98486a2d38
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221222"
---
# <a name="__readeflags"></a>__readeflags

讀取程式狀態和控制 (EFLAGS) 註冊。

## <a name="syntax"></a>語法

```C
unsigned     int __readeflags(void); /* x86 */
unsigned __int64 __readeflags(void); /* x64 */
```

## <a name="return-value"></a>傳回值

EFLAGS 註冊的值。 在32位平臺上, 傳回值為32位長, 而在64位平臺上則為64位長。

## <a name="remarks"></a>備註

這些常式僅供內建函式使用。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__readeflags`|x86、x64|

**標頭檔**\<intrin.h. h >

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)\
[__writeeflags](../intrinsics/writeeflags.md)
