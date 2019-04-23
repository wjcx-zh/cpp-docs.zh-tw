---
title: __writecr3
ms.date: 11/04/2016
f1_keywords:
- _writecr3
helpviewer_keywords:
- _writecr3 intrinsic
ms.assetid: 959d49fa-69d5-47cf-88d2-7688367fe38f
ms.openlocfilehash: 88467e4fb39abc9526e47a73f998d630470111a9
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59037363"
---
# <a name="writecr3"></a>__writecr3

**Microsoft 專屬**

將值寫入`Data`CR3 註冊。

## <a name="syntax"></a>語法

```
void writecr3(
   unsigned __int64 Data
);
```

#### <a name="parameters"></a>參數

*Data*<br/>
[in]要寫入的 CR3 暫存器的值。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__writecr3`|x86、x64|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

此內建只適用於核心模式，且此常式僅可作為內建常式使用。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)