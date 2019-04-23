---
title: __readcr4
ms.date: 11/04/2016
f1_keywords:
- __readcr4
helpviewer_keywords:
- __readcr4 intrinsic
ms.assetid: b841a27b-fe0d-4ee9-b76b-f91d3eb061fa
ms.openlocfilehash: b67016846768be778881c02b395c8d6f3af1ef3f
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59037213"
---
# <a name="readcr4"></a>__readcr4

**Microsoft 專屬**

讀取 CR4 暫存器，並傳回其值。

## <a name="syntax"></a>語法

```
unsigned __int64 __readcr4(void);
```

## <a name="return-value"></a>傳回值

CR4 暫存器中的值。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__readcr4`|x86、x64|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

此內建只適用於核心模式，且此常式僅可作為內建常式使用。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)