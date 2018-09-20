---
title: __wbinvd |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __wbinvd
dev_langs:
- C++
helpviewer_keywords:
- __wbinvd intrinsic
- wbinvd instruction
ms.assetid: 628d0981-39e5-49e1-bd43-706d123af121
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5a1f412de7c8752ba1c1ba1324d20e1d4fb4c6a7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46388377"
---
# <a name="wbinvd"></a>__wbinvd

**Microsoft 專屬**

產生的回寫和使其失效的快取 (`wbinvd`) 指令。

## <a name="syntax"></a>語法

```
void __wbinvd(void);
```

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__wbinvd`|x86、x64|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

此函式只適用於核心模式特殊權限層級 (CPL) 為 0，且此常式僅可作為內建。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)