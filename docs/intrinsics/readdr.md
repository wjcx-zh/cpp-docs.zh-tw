---
title: __readdr |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __readdr
dev_langs:
- C++
helpviewer_keywords:
- __readdr intrinsic
ms.assetid: 061b05da-c85e-4052-b392-106f14bb84f1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dffb51782e87903feaeb733765fcf9f4763a64f6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385140"
---
# <a name="readdr"></a>__readdr

讀取指定的偵錯暫存器的值。

## <a name="syntax"></a>語法

```
unsigned         __readdr(unsigned int DebugRegister);
unsigned __int64 __readdr(unsigned int DebugRegister);
```

#### <a name="parameters"></a>參數

*DebugRegister*<br/>
[in]從 0 到 7 可識別偵錯常數暫存器。

## <a name="return-value"></a>傳回值

指定的偵錯暫存器的值。

## <a name="remarks"></a>備註

這些內建函式是只適用於核心模式，而只提供內建函式常式。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__readdr`|x86、x64|

**標頭檔** \<intrin.h >

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)<br/>
[__readeflags](../intrinsics/readeflags.md)