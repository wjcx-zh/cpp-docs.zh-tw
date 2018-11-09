---
title: setvbuf 常數
ms.date: 11/04/2016
f1_keywords:
- _IOFBF
- _IONBF
- _IOLBF
helpviewer_keywords:
- _IOFBF constant
- IOFBF constant
- IONBF constant
- _IOLBF constant
- IOLBF constant
- _IONBF constant
ms.assetid: a6ec4dd5-1f24-498c-871a-e874cd28d33c
ms.openlocfilehash: 25c25741f54c1383a5bad9038b5b5d761dacdd89
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50458042"
---
# <a name="setvbuf-constants"></a>setvbuf 常數

## <a name="syntax"></a>語法

```

#include <stdio.h>

```

## <a name="remarks"></a>備註

這些常數表示 `setvbuf` 的緩衝區類型。

下列資訊清單常數會提供可能的值：

|常數|意義|
|--------------|-------------|
|`_IOFBF`|完整緩衝：會使用在 `setvbuf` 呼叫中所指定的緩衝區，且其大小會和 `setvbuf` 呼叫中所指定的大小相同。 如果緩衝區指標為 **NULL**，則會使用指定大小的自動配置緩衝區。|
|`_IOLBF`|與 `_IOFBF` 相同。|
|`_IONBF`|不使用緩衝區，不論 `setvbuf` 呼叫中的引數為何。|

## <a name="see-also"></a>請參閱

[setbuf](../c-runtime-library/reference/setbuf.md)<br/>
[全域常數](../c-runtime-library/global-constants.md)