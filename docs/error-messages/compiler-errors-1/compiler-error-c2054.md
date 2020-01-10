---
title: 編譯器錯誤 C2054
ms.date: 11/04/2016
f1_keywords:
- C2054
helpviewer_keywords:
- C2054
ms.assetid: 37f7c612-0d7d-4728-9e67-ac4160555f48
ms.openlocfilehash: e7d90d684c1d95f540f6357bf61ee7c6f889ad3f
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302051"
---
# <a name="compiler-error-c2054"></a>編譯器錯誤 C2054

必須是 ' （' 才能遵循 ' identifier '

函數識別碼用於需要尾端括弧的內容中。

這個錯誤可能是因為在複雜的初始化上省略等號（=）所造成。

下列範例會產生 C2054：

```c
// C2054.c
int array1[] { 1, 2, 3 };   // C2054, missing =
```

可能的解決方案：

```c
// C2054b.c
int main() {
   int array2[] = { 1, 2, 3 };
}
```
