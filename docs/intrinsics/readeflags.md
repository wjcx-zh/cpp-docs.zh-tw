---
title: __readeflags |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __readeflags
dev_langs:
- C++
helpviewer_keywords:
- __readeflags intrinsic
ms.assetid: f9d2f4d8-c428-491f-b8de-04d0566b2b6b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d32096f50561ad89b2c9fdc50ca3c7e00425bf86
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46447592"
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