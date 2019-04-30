---
title: __readeflags
ms.date: 11/04/2016
f1_keywords:
- __readeflags
helpviewer_keywords:
- __readeflags intrinsic
ms.assetid: f9d2f4d8-c428-491f-b8de-04d0566b2b6b
ms.openlocfilehash: 9913fb4287e673faf79b2c352bb42eda7f590fdd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396479"
---
# <a name="readeflags"></a>__readeflags

讀取的程式狀態和控制項 (EFLAGS) 註冊。

## <a name="syntax"></a>語法

```
unsigned     int __readeflags(void);
unsigned __int64 __readeflags(void);
```

## <a name="return-value"></a>傳回值

EFLAGS 暫存器的值。 傳回值是 32 位元長時間上的 32 位元平台和 64 位元長時間在 64 位元平台上。

## <a name="remarks"></a>備註

這些常式都僅有內建函式。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__readeflags`|x86、x64|

**標頭檔** \<intrin.h >

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)<br/>
[__writeeflags](../intrinsics/writeeflags.md)