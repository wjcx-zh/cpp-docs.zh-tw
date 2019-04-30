---
title: __readpmc
ms.date: 11/04/2016
f1_keywords:
- __readpmc
helpviewer_keywords:
- Read Performance Monitoring Counters instruction
- __readpmc intrinsic
- rdpmc instruction
ms.assetid: 14ed45a6-28b6-4635-8437-a597c04b43d4
ms.openlocfilehash: 848c880e76d6d431ee56a0bb30a33b276837ce76
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396440"
---
# <a name="readpmc"></a>__readpmc

**Microsoft 專屬**

會產生`rdpmc`指令，讀取效能監視所指定的計數器`counter`。

## <a name="syntax"></a>語法

```
unsigned __int64 __readpmc(
   unsigned long counter
);
```

#### <a name="parameters"></a>參數

*counter*<br/>
[in]要讀取的效能計數器。

## <a name="return-value"></a>傳回值

指定的效能計數器的值。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__readpmc`|x86、x64|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

此內建只適用於核心模式，且此常式僅可作為內建。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)