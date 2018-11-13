---
title: HUGE_VAL、_HUGE
ms.date: 11/04/2016
apiname:
- _HUGE
apilocation:
- msvcrt.dll
apitype: DLLExport
f1_keywords:
- _HUGE
- HUGE_VAL
helpviewer_keywords:
- _HUGE constant
- HUGE_VAL constant
- double value
ms.assetid: 3f044b45-02cd-46b2-b1de-87fd0441dd6a
ms.openlocfilehash: 8f8342990ea62b368b46ed56f0697a844c755a61
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2018
ms.locfileid: "51522125"
---
# <a name="hugeval-huge"></a>HUGE_VAL、_HUGE

## <a name="syntax"></a>語法

```

#include <math.h>
```

## <a name="remarks"></a>備註

`HUGE_VAL` 是最大的可表示雙精度浮點數值。 發生錯誤時，許多執行階段數學函式會傳回這個值。 針對某些函式，會傳回 -`HUGE_VAL`。 `HUGE_VAL` 定義為 `_HUGE`，但執行階段數學函式傳回 `HUGE_VAL`。 為保持一致性，您也應該在程式碼中使用 `HUGE_VAL`。

## <a name="see-also"></a>請參閱

[全域常數](../c-runtime-library/global-constants.md)