---
title: （_e) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _enable
- _enable_cpp
dev_langs:
- C++
helpviewer_keywords:
- enable intrinsic
- _enable intrinsic
- ssm instruction
ms.assetid: 8bee669b-6bd8-4e25-9383-bb7d57295b4d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce3b59bc6665c4622078285a0c3b4b5011bc7d9b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433372"
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