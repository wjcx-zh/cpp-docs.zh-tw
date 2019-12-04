---
title: 編譯器錯誤 C2589
ms.date: 11/04/2016
f1_keywords:
- C2589
helpviewer_keywords:
- C2589
ms.assetid: 1d7942c7-8a81-4bb4-b272-76a0019e8513
ms.openlocfilehash: 76cc35e57c1577ed23c043740f37c602600da542
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74748498"
---
# <a name="compiler-error-c2589"></a>編譯器錯誤 C2589

' identifier '： '：： ' 右邊有不合法的 token

如果類別、結構或等位名稱出現在範圍解析運算子的左邊（雙冒號），則右邊的 token 必須是類別、結構或等位成員。 否則，任何全域識別碼都可以出現在右側。

範圍解析運算子無法多載。

下列範例會產生 C2589：

```cpp
// C2589.cpp
void Test(){}
class A {};
void operator :: ();   // C2589

int main() {
   ::Test();
}
```
