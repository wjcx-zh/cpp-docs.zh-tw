---
title: __writecr0
ms.date: 11/04/2016
f1_keywords:
- _writecr0
helpviewer_keywords:
- _writecr0 intrinsic
ms.assetid: a143d08d-0333-4e1b-91b4-4acb2ae91b5a
ms.openlocfilehash: 24d9ffe0e07269fedf19f90a7c66a07e3c5e7d3e
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59039372"
---
# <a name="writecr0"></a>__writecr0

**Microsoft 專屬**

將值寫入`Data`至 CR0 暫存器。

## <a name="syntax"></a>語法

```
void writecr0(
   unsigned __int64 Data
);
```

#### <a name="parameters"></a>參數

*Data*<br/>
[in]要寫入的 CR0 暫存器的值。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__writecr0`|x86、x64|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

此內建只適用於核心模式，且此常式僅可作為內建常式使用。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)