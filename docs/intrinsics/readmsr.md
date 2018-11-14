---
title: __readmsr
ms.date: 11/04/2016
f1_keywords:
- __readmsr
helpviewer_keywords:
- Read Model Specific Register
- rdmsr instruction
- __readmsr intrinsic
ms.assetid: 7ab1f8e8-72cb-4ce4-817d-3e728a3c9716
ms.openlocfilehash: 891ca43af4a81b63de39d367ea418e43811f78d0
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51326403"
---
# <a name="readmsr"></a>__readmsr

**Microsoft 專屬**

會產生`rdmsr`的指示，它會讀取所指定的模型特定暫存`register`並傳回其值。

## <a name="syntax"></a>語法

```
__int64 __readmsr(
   int register
);
```

#### <a name="parameters"></a>參數

*register*<br/>
[in]讀取模型特定暫存器。

## <a name="return-value"></a>傳回值

指定的暫存器中的值。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__readmsr`|x86、x64|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

此函式只適用於核心模式，且此常式僅可作為內建。

如需詳細資訊，請參閱 AMD 文件。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)