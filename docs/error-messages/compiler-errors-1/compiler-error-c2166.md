---
title: 編譯器錯誤 C2166
ms.date: 11/04/2016
f1_keywords:
- C2166
helpviewer_keywords:
- C2166
ms.assetid: 12789c3a-cc76-48bb-ae2e-64283e0964ed
ms.openlocfilehash: 73b3c29c5e4bdd22a50330a8a90aad37a9d45cbf
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758407"
---
# <a name="compiler-error-c2166"></a>編譯器錯誤 C2166

左值 (l-value) 指定 const 物件

程式碼嘗試修改宣告為 `const`的項目。

下列範例會產生 C2166：

```cpp
// C2166.cpp
int f();
int main() {
   ( (const int&) 1 ) = 5;   // C2166
}
```
