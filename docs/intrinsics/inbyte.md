---
title: __inbyte
ms.date: 11/04/2016
f1_keywords:
- __inbyte
- __inbyte_cpp
helpviewer_keywords:
- in instruction
- __inbyte intrinsic
ms.assetid: 03b61799-2a08-474d-adc4-2cbf7c81a4d5
ms.openlocfilehash: 63d4e9229eb7c5058587975d0ea04696786a9c73
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50562145"
---
# <a name="inbyte"></a>__inbyte

**Microsoft 專屬**

會產生`in`的指示，傳回一個位元組讀取所指定的連接埠`Port`。

## <a name="syntax"></a>語法

```
unsigned char __inbyte(
   unsigned short Port
);
```

#### <a name="parameters"></a>參數

*連接埠*<br/>
[in]要讀取的連接埠。

## <a name="return-value"></a>傳回值

從指定的連接埠讀取的位元組。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__inbyte`|x86、x64|

**標頭檔** \<intrin.h >

**結束 Microsoft 專屬**

## <a name="remarks"></a>備註

此常式僅可作為內建常式使用。

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)