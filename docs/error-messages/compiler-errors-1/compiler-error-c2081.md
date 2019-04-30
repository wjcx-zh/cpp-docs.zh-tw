---
title: 編譯器錯誤 C2081
ms.date: 11/04/2016
f1_keywords:
- C2081
helpviewer_keywords:
- C2081
ms.assetid: 7db9892d-364d-4178-a49d-f8398ece09a0
ms.openlocfilehash: 2bccd15b8c2b6d1c5cd6c4b536bbdaf350eb0181
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408650"
---
# <a name="compiler-error-c2081"></a>編譯器錯誤 C2081

'identifier': 不合法的型式參數清單中的名稱

識別項會導致語法錯誤。

此錯誤可能被因使用舊樣式型式參數清單。 在型式參數清單中，您必須指定的型式參數的類型。

下列範例會產生 C2081:

```
// C2081.c
void func( int i, j ) {}  // C2081, no type specified for j
```

可能的解決方式：

```
// C2081b.c
// compile with: /c
void func( int i, int j ) {}
```