---
title: __outwordstring
ms.date: 09/02/2019
f1_keywords:
- __outwordstring
helpviewer_keywords:
- rep outsw instruction
- __outwordstring intrinsic
- outsw instruction
ms.assetid: b470c7a0-1de9-4370-886a-b2c3a1f842f4
ms.openlocfilehash: 3cc5b0ae2101c86e3dc899b7924ec2524f0ea6e7
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217115"
---
# <a name="__outwordstring"></a>__outwordstring

**Microsoft 專屬**

產生指令, 其會傳送從*Buffer*開始的計數位組, 以及*埠*所指定的 i/o 埠。 `rep outsw`

## <a name="syntax"></a>語法

```C
void __outwordstring(
   unsigned short Port,
   unsigned short* Buffer,
   unsigned long Count
);
```

### <a name="parameters"></a>參數

*移植*\
在要將資料傳送至其中的通訊埠。

*緩衝區*\
在要從指定的埠送出之資料的指標。

*計數*\
在要傳送的單字數目。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__outwordstring`|x86、x64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

此常式僅可作為內建常式使用。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
