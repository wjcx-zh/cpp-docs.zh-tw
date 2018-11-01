---
title: __indwordstring
ms.date: 11/04/2016
f1_keywords:
- __indwordstring
- __indwordstring_cpp
helpviewer_keywords:
- __indwordstring intrinsic
- rep insd instruction
ms.assetid: 96a1cf33-f691-4916-99e4-fa849b61e3a9
ms.openlocfilehash: 96ad1551eb51ab1a91127cf57c9bd7915b84c379
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50574390"
---
# <a name="indwordstring"></a>__indwordstring

**Microsoft 專屬**

使用指定的連接埠時，讀取資料`rep insd`指令。

## <a name="syntax"></a>語法

```
void __indwordstring(
   unsigned short Port,
   unsigned long* Buffer,
   unsigned long Count
);
```

#### <a name="parameters"></a>參數

*連接埠*<br/>
[in]要讀取的連接埠。

*Buffer*<br/>
[out]從連接埠讀取的資料會寫入此處。

*計數*<br/>
[in]要讀取之資料的位元組數目。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__indwordstring`|x86、x64|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

此常式僅可作為內建常式使用。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)