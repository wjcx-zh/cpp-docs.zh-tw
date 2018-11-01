---
title: __readcr8
ms.date: 11/04/2016
f1_keywords:
- __readcr8
helpviewer_keywords:
- __readcr8 intrinsic
ms.assetid: fce16953-87ff-4fbe-8081-7962b97ae46c
ms.openlocfilehash: 041d1b1574ff3d6d3f8bf14575758d1b3ea62e15
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50602799"
---
# <a name="readcr8"></a>__readcr8

**Microsoft 專屬**

讀取 CR8 暫存器，並傳回其值。

## <a name="syntax"></a>語法

```
unsigned __int64 __readcr8(void);
```

## <a name="return-value"></a>傳回值

CR8 暫存器中的值。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__readcr8`|X64|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

此內建只適用於核心模式，且此常式僅可作為內建常式使用。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)