---
title: 編譯器警告 (層級 1) C4540
ms.date: 11/04/2016
f1_keywords:
- C4540
helpviewer_keywords:
- C4540
ms.assetid: 8085e748-5f4d-43c2-b06d-eaf794edbf72
ms.openlocfilehash: 13935e7eebdf3e7b7e89fad8c55d410cf2788e4d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230645"
---
# <a name="compiler-warning-level-1-c4540"></a>編譯器警告 (層級 1) C4540

dynamic_cast 用來轉換成無法存取或不明確的基底;執行時間測試將會失敗（' type1 ' 至 ' type2 '）

您用 **`dynamic_cast`** 來從一種類型轉換成另一種。 編譯器判定轉換一律會失敗（傳回**Null**），因為基類無法存取（ **`private`** 例如）或不明確（例如，在類別階層中出現一次以上）。

以下顯示此警告的範例。 類別**B**衍生自類別**A**。程式會使用 **`dynamic_cast`** 將類別**b** （衍生類別）轉換成類別**A**，這一律會失敗，因為類別**b**是 **`private`** ，因此無法存取。 將的存取權**變更**為 **`public`** 將會解決警告。

```cpp
// C4540.cpp
// compile with: /W1

struct A {
   virtual void g() {}
};

struct B : private A {
   virtual void g() {}
};

int main() {
   B b;
   A * ap = dynamic_cast<A*>(&b);   // C4540
}
```
