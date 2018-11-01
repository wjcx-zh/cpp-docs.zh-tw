---
title: STACKSIZE
ms.date: 11/04/2016
f1_keywords:
- STACKSIZE
helpviewer_keywords:
- STACKSIZE .def file statement
ms.assetid: 4d8c79bd-1cb4-4e4d-90f2-b5a7a4d20e7a
ms.openlocfilehash: de2aa99375f588d682b714632590ba8e0db8ddcb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50597219"
---
# <a name="stacksize"></a>STACKSIZE

設定堆疊的大小 (以位元組為單位)。

```
STACKSIZE reserve[,commit]
```

## <a name="remarks"></a>備註

若要將堆疊相等的方法是使用[堆疊配置](../../build/reference/stack-stack-allocations.md)(/stack) 選項。 如需詳細資訊，該選項的相關文件請參閱關於*保留*和`commit`引數。

此選項沒有 Dll 不會影響。

## <a name="see-also"></a>另請參閱

[模組定義陳述式的規則](../../build/reference/rules-for-module-definition-statements.md)