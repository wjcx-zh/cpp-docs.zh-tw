---
title: signal 動作常數
ms.date: 11/04/2016
f1_keywords:
- SIG_IGN
- SIG_DFL
helpviewer_keywords:
- signal action constants
- SIG_IGN constant
- SIG_DFL constant
ms.assetid: c3cb4f15-d39e-4d9d-84f9-0d33e3eb5993
ms.openlocfilehash: 71c2eb796680e90cd16b1798fd478506ce7aa2c9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50444651"
---
# <a name="signal-action-constants"></a>signal 動作常數

接收到插斷訊號時會採取的動作，需視 `func` 的值而定。

## <a name="syntax"></a>語法

```
#include <signal.h>
```

## <a name="remarks"></a>備註

`func` 引數必須是函式位址，或是列於下方並在 SIGNAL.H 中定義的其中一個資訊清單常數。

|||
|-|-|
| `SIG_DFL`  | 使用系統預設回應。 如果呼叫端程式使用資料流 I/O，則不會清除由執行階段程式庫所建立的緩衝區。  |
| `SIG_IGN`  | 忽略插斷訊號。 這個值一律不應提供給 `SIGFPE`，因為處理序的浮點狀態未定義。  |
| `SIG_SGE`  | 指出訊號中發生錯誤。  |
| `SIG_ACK`  | 指出已收到通知。  |
| `SIG_ERR`  | 指出已發生錯誤之訊號的傳回類型。  |

## <a name="see-also"></a>請參閱

[signal](../c-runtime-library/reference/signal.md)<br/>
[全域常數](../c-runtime-library/global-constants.md)