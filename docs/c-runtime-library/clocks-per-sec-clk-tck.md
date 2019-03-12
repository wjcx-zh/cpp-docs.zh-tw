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
ms.openlocfilehash: eef065ac4fcedf13f3a5d54d4df0563fd04ef965
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57750672"
---
# <a name="clockspersec-clktck"></a>CLOCKS_PER_SEC、CLK_TCK

## <a name="syntax"></a>語法

```
#include <time.h>
```

## <a name="remarks"></a>備註

以秒為單位的時間，是由 `clock` 函式所傳回並除以 `CLOCKS_PER_SEC` 的值。 `CLK_TCK` 和它相等，但已被視為過時。

## <a name="see-also"></a>另請參閱

[時鐘](../c-runtime-library/reference/clock.md)<br/>
[全域常數](../c-runtime-library/global-constants.md)
