---
title: _enable
ms.date: 11/04/2016
f1_keywords:
- _enable
- _enable_cpp
helpviewer_keywords:
- enable intrinsic
- _enable intrinsic
- ssm instruction
ms.assetid: 8bee669b-6bd8-4e25-9383-bb7d57295b4d
ms.openlocfilehash: 1d129db17b489972555efb0b5df2de52e01fa649
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631230"
---
# <a name="enable"></a>_enable

**Microsoft 專屬**

啟用中斷。

## <a name="syntax"></a>語法

```
void _enable(void);
```

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`_enable`|x86、 x64、 ARM|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

`_enable` 指示處理器設定中斷旗標。 在 x86 系統中，這個函式會產生設定中斷旗標 (`sti`) 指令。

這個函式只適用於核心模式。 如果在使用者模式中使用，會擲回有權限指令例外狀況。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)