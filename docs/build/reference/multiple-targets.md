---
title: 多重目標
ms.date: 11/04/2016
helpviewer_keywords:
- makefiles, targets
- multiple targets in NMAKE
- targets, multiple in NMAKE
- NMAKE program, targets
ms.assetid: b609a179-0b9f-4b08-9930-998047588ae0
ms.openlocfilehash: 43e5216d5e11e89aff9b6f0c69ff4e76a8cc9da8
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57824715"
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

[目標](targets.md)
