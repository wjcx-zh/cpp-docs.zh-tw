---
title: __inword
ms.date: 09/02/2019
f1_keywords:
- __inword_cpp
- __inword
helpviewer_keywords:
- in instruction
- __inword intrinsic
ms.assetid: 5c617edd-6709-40a1-aad2-40d5e39283c6
ms.openlocfilehash: 7daaf1abd5089716061f118e30e9534e5c5c18ee
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440972"
---
# <a name="__inword"></a>__inword

**Microsoft 專屬**

使用 `in` 指令，從指定的埠讀取資料。

## <a name="syntax"></a>語法

```C
unsigned short __inword(
   unsigned short Port
);
```

### <a name="parameters"></a>參數

*埠*\
在要從中讀取的埠。

## <a name="return-value"></a>傳回值

讀取的資料字。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__inword`|x86、x64|

**標頭檔**\<intrin.h >

## <a name="remarks"></a>備註

此常式僅可作為內建常式使用。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
