---
title: STACKSIZE
ms.date: 11/04/2016
f1_keywords:
- STACKSIZE
helpviewer_keywords:
- STACKSIZE .def file statement
ms.assetid: 4d8c79bd-1cb4-4e4d-90f2-b5a7a4d20e7a
ms.openlocfilehash: 5f0c23ad8b8d81f888616042ee5d6ba5bc63bd44
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57412870"
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
