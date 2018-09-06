---
title: 字元化運算子 (#@) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '#@'
dev_langs:
- C++
helpviewer_keywords:
- preprocessor, operators
- charizing operator
- '#@ preprocessor operator'
ms.assetid: dee03314-d27c-4063-965c-64756efbef22
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d86c49c8d7d0cda91ba2415167cc79c810a96b3d
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43895301"
---
# <a name="charizing-operator-"></a>字元化運算子 (#@)
**Microsoft 專屬**

字元化運算子只能搭配巨集的引數使用。 如果`#@`出現在型式參數之前在巨集的定義中，實際的引數是以單引號括住，而且視為字元時就會展開巨集。 例如: 

```
#define makechar(x)  #@x
```

會使陳述式

```
a = makechar(b);
```

展開成

```
a = 'b';
```

單一引號字元不能與字元化運算子搭配使用。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[前置處理器運算子](../preprocessor/preprocessor-operators.md)