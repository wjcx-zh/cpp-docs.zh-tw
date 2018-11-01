---
title: 多重目標
ms.date: 11/04/2016
helpviewer_keywords:
- makefiles, targets
- multiple targets in NMAKE
- targets, multiple in NMAKE
- NMAKE program, targets
ms.assetid: b609a179-0b9f-4b08-9930-998047588ae0
ms.openlocfilehash: 2762e458781e3a95f478ea3477fc8ef02f9196fb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50645052"
---
# <a name="multiple-targets"></a>多重目標

如同每個個別描述區塊中指定，NMAKE 就會評估成單一的相依性的多個目標。

例如，這個...

```Output
bounce.exe leap.exe : jump.obj
   echo Building...
```

...已評估為此：

```Output
bounce.exe : jump.obj
   echo Building...
leap.exe : jump.obj
   echo Building...
```

## <a name="see-also"></a>另請參閱

[目標](../build/targets.md)