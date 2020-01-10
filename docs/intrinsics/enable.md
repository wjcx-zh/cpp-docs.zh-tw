---
title: _enable
ms.date: 09/02/2019
f1_keywords:
- _enable
- _enable_cpp
helpviewer_keywords:
- enable intrinsic
- _enable intrinsic
- ssm instruction
ms.assetid: 8bee669b-6bd8-4e25-9383-bb7d57295b4d
ms.openlocfilehash: 7adcd4eac807b8d0937efbbe6d89f8ad6dcb157c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217879"
---
# <a name="_enable"></a>_enable

**Microsoft 專屬**

啟用中斷。

## <a name="syntax"></a>語法

```C
void _enable(void);
```

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`_enable`|x86、ARM、x64、ARM64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

`_enable` 指示處理器設定中斷旗標。 在 x86 系統中，這個函式會產生設定中斷旗標 (`sti`) 指令。

這個函式只適用於核心模式。 如果在使用者模式中使用，會擲回有權限指令例外狀況。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)
