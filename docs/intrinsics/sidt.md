---
title: __sidt
ms.date: 09/02/2019
f1_keywords:
- __sidt
helpviewer_keywords:
- sidt instruction
- __sidt intrinsic
ms.assetid: 01e83d14-6e63-4dea-8f64-5a0339d69641
ms.openlocfilehash: d6b685da0e02373307a3149c5b7b28213f37ad40
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222320"
---
# <a name="__sidt"></a>__sidt

**Microsoft 專屬**

將中斷描述項資料表暫存器 (IDTR) 的值儲存在指定的記憶體位置。

## <a name="syntax"></a>語法

```C
void __sidt(void * Destination);
```

### <a name="parameters"></a>參數

*位置*\
在儲存 IDTR 之記憶體位置的指標。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__sidt`|x86、x64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

`__sidt` 函式相當於 `SIDT` 機器指令。 如需詳細資訊, 請搜尋檔「Intel 架構軟體發展人員手冊, 第2卷:指示集參考, 位於[Intel Corporation](https://software.intel.com/articles/intel-sdm)網站。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)\
[__lidt](../intrinsics/lidt.md)
