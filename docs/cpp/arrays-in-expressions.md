---
title: 運算式中的陣列
ms.date: 11/04/2016
helpviewer_keywords:
- expressions [C++], arrays in
- arrays [C++], in expressions
ms.assetid: 6e5a795b-d6bd-4e39-b313-6a20d47c4d4b
ms.openlocfilehash: 0f2ef43c2a5bc4f8a44378c21d6d53b14f07ea07
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50478165"
---
# <a name="arrays-in-expressions"></a>運算式中的陣列

當陣列型別的識別項出現在運算式中以外`sizeof`，傳址 (**&**)，或初始化的參考，則會轉換成第一個陣列元素的指標。 例如: 

```cpp
char szError1[] = "Error: Disk drive not ready.";
char *psz = szError1;
```

指標 `psz` 會指向陣列 `szError1` 的第一個元素。 請注意，陣列 (和指標不同) 不是可修改的左值。 因此，下列指派是不合法的：

```cpp
szError1 = psz;
```

## <a name="see-also"></a>另請參閱

[陣列](../cpp/arrays-cpp.md)