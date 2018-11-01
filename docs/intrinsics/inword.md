---
title: __inword
ms.date: 11/04/2016
f1_keywords:
- __indword_cpp
- __indword
helpviewer_keywords:
- in instruction
- __inword intrinsic
ms.assetid: 5c617edd-6709-40a1-aad2-40d5e39283c6
ms.openlocfilehash: 85498fd85f5401ad123794cc9aaed2b278db867c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50475357"
---
# <a name="inword"></a>__inword

**Microsoft 專屬**

使用指定的連接埠時，讀取資料`in`指令。

## <a name="syntax"></a>語法

```
unsigned short __inword(
   unsigned short Port
);
```

#### <a name="parameters"></a>參數

*連接埠*<br/>
[in]要讀取的連接埠。

## <a name="return-value"></a>傳回值

讀取資料的文字。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__inword`|x86、x64|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

此常式僅可作為內建常式使用。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)