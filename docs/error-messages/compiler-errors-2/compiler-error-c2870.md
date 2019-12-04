---
title: 編譯器錯誤 C2870
ms.date: 11/04/2016
f1_keywords:
- C2870
helpviewer_keywords:
- C2870
ms.assetid: 80523ee9-1fd3-4dc4-8a77-5083deb99066
ms.openlocfilehash: 3b006592723df1222d05e39b3bc9e5729efc8aa6
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755027"
---
# <a name="compiler-error-c2870"></a>編譯器錯誤 C2870

' name '：命名空間定義必須出現在檔案範圍，或緊接在另一個命名空間定義中

您定義的命名空間 `name` 不正確。 命名空間必須定義于檔案範圍（在所有區塊和類別之外），或緊接在另一個命名空間內。

下列範例會產生 C2870：

```cpp
// C2870.cpp
// compile with: /c
int main() {
   namespace A { int i; };   // C2870
}
```
