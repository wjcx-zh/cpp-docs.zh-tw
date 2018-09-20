---
title: __writedr |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __writedr
dev_langs:
- C++
helpviewer_keywords:
- __writedr intrinsic
ms.assetid: ac55c1ee-df2f-41d4-a429-6f369d2a934d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5fd9bd5145947711c245f552672843d604160d06
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46402165"
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