---
title: _disable |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _disable_cpp
- _disable
dev_langs:
- C++
helpviewer_keywords:
- _disable intrinsic
- rsm instruction
- disable intrinsic
ms.assetid: 52da3df9-815c-4524-9839-6d1742cff5c6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e2e0eb09934847c2f7b67c9e4961b02d31c68df2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46382410"
---
# <a name="disable"></a>_disable

**Microsoft 專屬**

停用中斷。

## <a name="syntax"></a>語法

```
void _disable(void);
```

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`_disable`|x86、 x64、 ARM|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

`_disable` 指示處理器清除中斷旗標。 在 x86 系統中，這個函式會產生清除中斷旗標 (`cli`) 指令。

這個函式只適用於核心模式。 如果在使用者模式中使用，會在執行階段擲回有權限指令例外狀況。

在 ARM 平台上，此常式僅可作為內建常式使用。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)