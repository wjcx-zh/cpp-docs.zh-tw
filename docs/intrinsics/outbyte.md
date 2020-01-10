---
title: __outbyte
ms.date: 09/02/2019
f1_keywords:
- __outbyte
helpviewer_keywords:
- out instruction
- __outbyte intrinsic
ms.assetid: c4cd1a34-8a02-4e37-993d-3201bc17901a
ms.openlocfilehash: 18792010c45ffb648e9555ccb73f8614c3e3e6ea
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217203"
---
# <a name="__outbyte"></a>__outbyte

**Microsoft 專屬**

產生指令, 這會傳送由`Data`所指定`Port`的 i/o 埠所指定的1個位元組。 `out`

## <a name="syntax"></a>語法

```C
void __outbyte(
   unsigned short Port,
   unsigned char Data
);
```

### <a name="parameters"></a>參數

*移植*\
在要將資料傳送至其中的通訊埠。

*Data*\
在要從指定的埠送出的位元組。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__outbyte`|x86、x64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

此常式僅可作為內建常式使用。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
