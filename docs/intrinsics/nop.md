---
title: __nop
ms.date: 11/04/2016
f1_keywords:
- __nop
helpviewer_keywords:
- nop instruction
- __nop intrinsic
ms.assetid: 7a2a938b-87e0-476d-a348-03ea7635b6b9
ms.openlocfilehash: 25ba27485990ceaae77e1827f0c74680914e2f40
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651720"
---
# <a name="nop"></a>__nop

**Microsoft 專屬**

產生會執行任何作業的平台專屬電腦程式碼。

## <a name="syntax"></a>語法

```
void __nop();
```

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__nop`|x86、x64|

**標頭檔** \<intrin.h >

**結束 Microsoft 專屬**

## <a name="remarks"></a>備註

`__nop` 函式相當於 `NOP` 機器指令。 如需詳細資訊，搜尋文件中，「 Intel 架構軟體開發人員的手動、 磁碟區 2： 指令集參考，「 在[Intel Corporation](https://software.intel.com/articles/intel-sdm)站台。

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)<br/>
[__noop](../intrinsics/noop.md)