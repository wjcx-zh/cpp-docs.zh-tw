---
title: __outdwordstring
ms.date: 09/02/2019
f1_keywords:
- __outdwordstring
helpviewer_keywords:
- outsd instruction
- __outdwordstring intrinsic
- rep outsd instruction
ms.assetid: 55b31a65-aab7-4b5c-b61d-d9e2fb0c497a
ms.openlocfilehash: 50908a65795af617f18a497c073cfefe009dfd80
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217157"
---
# <a name="__outdwordstring"></a>__outdwordstring

**Microsoft 專屬**

產生指令, `Count`這會從所指定`Port`的`Buffer` i/o 埠開始傳送雙字。 `rep outsd`

## <a name="syntax"></a>語法

```C
void __outdwordstring(
   unsigned short Port,
   unsigned long* Buffer,
   unsigned long Count
);
```

### <a name="parameters"></a>參數

*移植*\
在要將資料傳送至其中的通訊埠。

*緩衝區*\
在要從指定的埠送出之資料的指標。

*計數*\
在要傳送的雙用字數。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__outdwordstring`|x86、x64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

此常式僅可作為內建常式使用。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
