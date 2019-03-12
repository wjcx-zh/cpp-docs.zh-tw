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
ms.openlocfilehash: 28c9debf7e51d06cb9a625bb0a52d578ce3142c6
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57742650"
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
|`_IOFBF`|完整緩衝︰將會使用對 `setvbuf` 之呼叫中所指定的緩衝區，而其大小則如 `setvbuf` 呼叫中所指定。 如果緩衝區指標為 **NULL**，則會使用指定大小的自動配置緩衝區。|
|`_IOLBF`|與 `_IOFBF` 相同。|
|`_IONBF`|不使用緩衝區，不論 `setvbuf` 呼叫中的引數為何。|

## <a name="see-also"></a>另請參閱

[setbuf](../c-runtime-library/reference/setbuf.md)<br/>
[全域常數](../c-runtime-library/global-constants.md)
