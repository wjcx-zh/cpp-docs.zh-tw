---
title: 累計相依性
ms.date: 11/04/2016
helpviewer_keywords:
- dependencies, cumulative
- cumulative dependencies in NMAKE
- dependencies
ms.assetid: fa6dd777-80b8-437d-87a7-aec0ed818a49
ms.openlocfilehash: c31740b830993c91568aea6d167fd3113b04fc57
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50460277"
---
# <a name="cumulative-dependencies"></a>累計相依性

相依性是累計描述區塊中，如果目標會重複。

比方說，這組規則，

```Output
bounce.exe : jump.obj
bounce.exe : up.obj
   echo Building bounce.exe...
```

會評估為此：

```Output
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
```

如同在不同的描述區塊中，指定每個，但是不會在最後一行中，相依性的目標不會使用的命令區塊，會評估單一描述區塊中的多個相依性命令行中的多個目標。 NMAKE 會嘗試推斷規則用於這類目標。

比方說，這組規則，

```Output
leap.exe bounce.exe : jump.obj
bounce.exe climb.exe : up.obj
   echo Building bounce.exe...
```

會評估為此：

```Output

leap.exe : jump.obj
# invokes an inference rule
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
climb.exe : up.obj
   echo Building bounce.exe...
```

## <a name="see-also"></a>另請參閱

[目標](../build/targets.md)