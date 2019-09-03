---
title: __halt
ms.date: 09/02/2019
f1_keywords:
- __halt
- __halt_cpp
helpviewer_keywords:
- __halt intrinsic
- HLT instruction
ms.assetid: a074f44a-101c-45a5-8a5e-cfd223c34002
ms.openlocfilehash: 66f5e05e7673523966ef35ac743fc585930b511c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222158"
---
# <a name="__halt"></a>__halt

**Microsoft 專屬**

停止微處理器, 直到啟用的插斷、nonmaskable 插斷 (NMI) 或重設發生為止。

## <a name="syntax"></a>語法

```C
void __halt( void );
```

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__halt`|x86、x64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

函式相當`HLT`于機器指令, 而且只能在核心模式中使用。 `__halt` 如需詳細資訊, 請搜尋檔「Intel 架構軟體發展人員手冊, 第2卷:指示集參考, 位於[Intel Corporation](https://software.intel.com/articles/intel-sdm)網站。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
