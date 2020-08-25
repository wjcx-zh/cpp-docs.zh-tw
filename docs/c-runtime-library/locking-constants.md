---
title: _locking 常數
ms.date: 11/04/2016
f1_keywords:
- _LK_RLCK
- _LK_NBLCK
- _LK_LOCK
- _LK_NBRLCK
- _LK_UNLCK
helpviewer_keywords:
- LK_UNLCK constant
- LK_NBRLCK constant
- _LK_NBRLCK constant
- _LK_NBLCK constant
- _LK_LOCK constant
- LK_NBLCK constant
- _LK_UNLCK constant
- LK_RLCK constant
- _LK_RLCK constant
- LK_LOCK constant
ms.assetid: c3dc92c8-60e3-4d29-9f50-5d217627c8ad
ms.openlocfilehash: 8cfc1f933179e043f464a69f3ac5cf4ca25763e0
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88830822"
---
# <a name="_locking-constants"></a>_locking 常數

## <a name="syntax"></a>語法

```
#include <sys/locking.h>
```

## <a name="remarks"></a>備註

針對 `_locking` 函式呼叫中的 *mode* 引數中會指定要執行的鎖定動作。

*mode* 引數必須是下列其中一個資訊清單常數。

|值|描述|
|-|-|
| `_LK_LOCK`  | 鎖定指定的位元組。 如果無法鎖定位元組，函式會在 1 秒後重試。 如果嘗試 10 次之後還是無法鎖定位元組，函式會傳回錯誤。  |
| `_LK_RLCK`  | 與 `_LK_LOCK` 相同。  |
|`_LK_NBLCK`  | 鎖定指定的位元組。 如果無法鎖定位元組，函式會傳回錯誤。  |
| `_LK_NBRLCK`  | 與 `_LK_NBLCK` 相同。  |
| `_LK_UNLCK`  | 解除指定位元組的鎖定。 (位元組先前必須為已鎖定)。  |

## <a name="see-also"></a>另請參閱

[_locking](../c-runtime-library/reference/locking.md)<br/>
[全域常數](../c-runtime-library/global-constants.md)
