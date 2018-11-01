---
title: __readeflags
ms.date: 11/04/2016
f1_keywords:
- __readeflags
helpviewer_keywords:
- __readeflags intrinsic
ms.assetid: f9d2f4d8-c428-491f-b8de-04d0566b2b6b
ms.openlocfilehash: e5294180904d0d7ca3bbd1de75e45e058a33c88f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594260"
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