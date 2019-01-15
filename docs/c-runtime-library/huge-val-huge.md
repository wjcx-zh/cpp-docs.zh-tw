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
ms.openlocfilehash: b1d9b099684d9671a60dd1afb1e6692e3c0d2a65
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220474"
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
