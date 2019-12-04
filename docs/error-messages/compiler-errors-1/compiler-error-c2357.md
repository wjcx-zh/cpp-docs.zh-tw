---
title: 編譯器錯誤 C2357
ms.date: 11/04/2016
f1_keywords:
- C2357
helpviewer_keywords:
- C2357
ms.assetid: d1083945-0ea2-4385-9e66-8c665978806c
ms.openlocfilehash: ce1926468bac7e44485be5c0a0944fdf12dce3d8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759915"
---
# <a name="compiler-error-c2357"></a>編譯器錯誤 C2357

' identifier '：必須是類型 ' type ' 的函式

您的程式碼會宣告不符合編譯器在內部宣告之版本的 `atexit` 函數版本。 宣告 `atexit`，如下所示：

```
int __cdecl atexit(void (__cdecl *)());
```

如需詳細資訊，請參閱[init_seg](../../preprocessor/init-seg.md)。

下列範例會產生 C2357：

```cpp
// C2357.cpp
// compile with: /c
// C2357 expected
#pragma warning(disable : 4075)
// Uncomment the following line to resolve.
// int __cdecl myexit(void (__cdecl *)());
#pragma init_seg(".mine$m",myexit)
```
