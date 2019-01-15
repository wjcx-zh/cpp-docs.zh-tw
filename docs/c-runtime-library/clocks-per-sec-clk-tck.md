---
title: CLOCKS_PER_SEC、CLK_TCK
ms.date: 11/04/2016
f1_keywords:
- CLOCKS_PER_SEC
- CLK_TCK
helpviewer_keywords:
- CLOCKS_PER_SEC
- CLK_TCK constant
ms.assetid: bc285106-383d-44cb-91bf-276ad7de57bf
ms.openlocfilehash: a604425809f43be238cbcc7b9148782bb937e00f
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220357"
---
# <a name="clockspersec-clktck"></a>CLOCKS_PER_SEC、CLK_TCK

## <a name="syntax"></a>語法

```
#include <time.h>
```

## <a name="remarks"></a>備註

以秒為單位的時間，是由 `clock` 函式所傳回並除以 `CLOCKS_PER_SEC` 的值。 `CLK_TCK` 和它相等，但已被視為過時。

## <a name="see-also"></a>請參閱

[時鐘](../c-runtime-library/reference/clock.md)<br/>
[全域常數](../c-runtime-library/global-constants.md)
