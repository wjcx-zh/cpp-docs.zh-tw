---
title: __writeeflags
ms.date: 11/04/2016
f1_keywords:
- __writeeflags
helpviewer_keywords:
- __writeeflags intrinsics
ms.assetid: a62a522c-d7fa-4f10-a620-a3b32bdf3f17
ms.openlocfilehash: 8509bf37019d1525cdaca33bf1819d85ace7d75a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50600040"
---
# <a name="writeeflags"></a>__writeeflags

指定的值寫入程式狀態和控制 (EFLAGS) 註冊。

## <a name="syntax"></a>語法

```
void __writeeflags(unsigned Value);
void __writeeflags(unsigned __int64 Value);
```

#### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*值*|[in]要寫入的 EFLAGS 暫存器的值。 `Value`參數是 32 位元長，不適用於 32 位元平台和 64 位元長，不適用於 64 位元平台。|

## <a name="remarks"></a>備註

這些常式都僅有內建函式。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__writeeflags`|x86、x64|

**標頭檔** \<intrin.h >

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)<br/>
[__readeflags](../intrinsics/readeflags.md)