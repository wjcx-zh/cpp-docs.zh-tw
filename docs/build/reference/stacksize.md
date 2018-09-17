---
title: STACKSIZE |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- STACKSIZE
dev_langs:
- C++
helpviewer_keywords:
- STACKSIZE .def file statement
ms.assetid: 4d8c79bd-1cb4-4e4d-90f2-b5a7a4d20e7a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7d9b61febedde1a2647df6312a8588b08c6bdad7
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705558"
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