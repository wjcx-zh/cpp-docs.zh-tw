---
title: 相依性的副作用 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dependencies, side effects
- NMAKE program, dependents
ms.assetid: d4e8db25-fdc0-4d73-81ec-1538f2e1b3e8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9a70df679434b187bc2eee4eb4aad5881db0da1c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716512"
---
# <a name="dependency-side-effects"></a>相依性的副作用

如果以冒號 （:） 在不同的位置的兩個相依性命令行中指定目標，則命令會顯示後只是其中一條線 NMAKE 相鄰或合併時，就會解譯相依性。 它不會叫用的推斷規則，相依性沒有任何命令，但改為假設隸屬於一個描述區塊之相依性，以及執行其他相依性所指定的命令。 比方說，這組規則：

```Output
bounce.exe : jump.obj
   echo Building bounce.exe...

bounce.exe : up.obj
```

會評估為此：

```Output
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
```

這種效果不會發生雙冒號 (`::`) 使用。 比方說，這組規則：

```Output
bounce.exe :: jump.obj
   echo Building bounce.exe...

bounce.exe :: up.obj
```

會評估為此：

```Output
bounce.exe : jump.obj
   echo Building bounce.exe...

bounce.exe : up.obj
# invokes an inference rule
```

## <a name="see-also"></a>另請參閱

[目標](../build/targets.md)