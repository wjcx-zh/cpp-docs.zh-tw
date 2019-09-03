---
title: __inbyte
ms.date: 09/02/2019
f1_keywords:
- __inbyte
- __inbyte_cpp
helpviewer_keywords:
- in instruction
- __inbyte intrinsic
ms.assetid: 03b61799-2a08-474d-adc4-2cbf7c81a4d5
ms.openlocfilehash: f0036763ed7315a54fbfe6dcc873b46b52f0730c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222135"
---
# <a name="__inbyte"></a>__inbyte

**Microsoft 專屬**

產生指令, 傳回從`Port`指定的埠讀取的單一位元組。 `in`

## <a name="syntax"></a>語法

```C
unsigned char __inbyte(
   unsigned short Port
);
```

### <a name="parameters"></a>參數

*移植*\
在要從中讀取的埠。

## <a name="return-value"></a>傳回值

從指定的埠讀取的位元組。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__inbyte`|x86、x64|

**標頭檔**\<intrin.h. h >

**結束 Microsoft 專屬**

## <a name="remarks"></a>備註

此常式僅可作為內建常式使用。

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
