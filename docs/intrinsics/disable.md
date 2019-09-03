---
title: _disable
ms.date: 09/02/2019
f1_keywords:
- _disable_cpp
- _disable
helpviewer_keywords:
- _disable intrinsic
- rsm instruction
- disable intrinsic
ms.assetid: 52da3df9-815c-4524-9839-6d1742cff5c6
ms.openlocfilehash: 94be850e1d494ff62df84922b46f28481be68314
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216827"
---
# <a name="_disable"></a>_disable

**Microsoft 專屬**

停用中斷。

## <a name="syntax"></a>語法

```C
void _disable(void);
```

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`_disable`|x86、ARM、x64、ARM64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

`_disable` 指示處理器清除中斷旗標。 在 x86 系統中，這個函式會產生清除中斷旗標 (`cli`) 指令。

這個函式只適用於核心模式。 如果在使用者模式中使用，會在執行階段擲回有權限指令例外狀況。

在 ARM 和 ARM64 平臺上, 此常式僅以內建函式的形式提供。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
