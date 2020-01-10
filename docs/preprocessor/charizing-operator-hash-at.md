---
title: 字元化運算子 (#@)
ms.date: 08/29/2019
f1_keywords:
- '#@'
helpviewer_keywords:
- preprocessor, operators
- charizing operator
- '#@ preprocessor operator'
ms.assetid: dee03314-d27c-4063-965c-64756efbef22
ms.openlocfilehash: cb2a4e07287edf5ed2d0850ec7d870c8ef307879
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218541"
---
# <a name="charizing-operator-"></a>字元化運算子 (#@)

**Microsoft 專屬**

字元化運算子只能搭配巨集的引數使用。 如果`#@`在巨集定義中的型式參數之前, 會以單引號括住實質引數, 並在展開宏時將其視為字元。 例如：

```cpp
#define makechar(x)  #@x
```

會使陳述式

```cpp
a = makechar(b);
```

展開成

```cpp
a = 'b';
```

單引號字元 (`'`) 不能與字元化運算子搭配使用。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[預處理器運算子](../preprocessor/preprocessor-operators.md)
