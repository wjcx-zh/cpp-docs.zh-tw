---
title: 編譯器錯誤 C2879
ms.date: 11/04/2016
f1_keywords:
- C2879
helpviewer_keywords:
- C2879
ms.assetid: ac92b645-2394-49de-8632-43d44e0553ed
ms.openlocfilehash: 6c7238faf94a2493894534ae5684634b65bb4342
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74736291"
---
# <a name="compiler-error-c2879"></a>編譯器錯誤 C2879

' symbol '：只有現有的命名空間可以透過命名空間別名定義提供替代名稱

您無法在命名空間以外的符號上建立[命名空間別名](../../cpp/namespaces-cpp.md#namespace_aliases)。

下列範例會產生 C2879：

```cpp
// C2879.cpp
int main() {
   int i;
   namespace A = i;   // C2879 i is not a namespace
}
```
