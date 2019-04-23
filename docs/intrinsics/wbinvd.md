---
title: __wbinvd
ms.date: 11/04/2016
f1_keywords:
- __wbinvd
helpviewer_keywords:
- __wbinvd intrinsic
- wbinvd instruction
ms.assetid: 628d0981-39e5-49e1-bd43-706d123af121
ms.openlocfilehash: 99c7a452e063dea328e4aa1362aae8783929deb0
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59039263"
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