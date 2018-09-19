---
title: 運算式中的陣列 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- expressions [C++], arrays in
- arrays [C++], in expressions
ms.assetid: 6e5a795b-d6bd-4e39-b313-6a20d47c4d4b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 34f8a45dfa9de9a5a48e13cb6a38f667e5963f2d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068542"
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