---
title: 多重描述區塊中的目標 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- description blocks
- blocks, multiple description
- multiple description blocks
ms.assetid: 8618dcd9-c11d-4562-91a7-0c904ed438a8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f339561e0a1e8c94063aa0c36c3ecbc96545b35f
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722770"
---
# <a name="targets-in-multiple-description-blocks"></a>多重描述區塊中的目標

若要更新的目標使用不同的命令的多個描述區塊中，指定兩個連續冒號 （:） 之間的目標和相依項目。

```
target.lib :: one.asm two.asm three.asm
    ml one.asm two.asm three.asm
    lib target one.obj two.obj three.obj
target.lib :: four.c five.c
    cl /c four.c five.c
    lib target four.obj five.obj
```

## <a name="see-also"></a>另請參閱

[目標](../build/targets.md)