---
title: STACKSIZE
ms.date: 11/04/2016
f1_keywords:
- STACKSIZE
helpviewer_keywords:
- STACKSIZE .def file statement
ms.assetid: 4d8c79bd-1cb4-4e4d-90f2-b5a7a4d20e7a
ms.openlocfilehash: 2d27b4fd596098f4abc5bb0d804d87bd08f70a60
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318351"
---
# <a name="stacksize"></a>STACKSIZE

設定堆疊的大小 (以位元組為單位)。

```
STACKSIZE reserve[,commit]
```

## <a name="remarks"></a>備註

若要將堆疊相等的方法是使用[堆疊配置](stack-stack-allocations.md)(/stack) 選項。 如需詳細資訊，該選項的相關文件請參閱關於*保留*和`commit`引數。

此選項沒有 Dll 不會影響。

## <a name="see-also"></a>另請參閱

[模組定義陳述式的規則](rules-for-module-definition-statements.md)
