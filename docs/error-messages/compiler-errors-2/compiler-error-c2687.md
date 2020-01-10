---
title: 編譯器錯誤 C2687
ms.date: 11/04/2016
f1_keywords:
- C2687
helpviewer_keywords:
- C2687
ms.assetid: 1d24b24a-cd0f-41cc-975c-b08dcfb7f402
ms.openlocfilehash: f3e728033a3230d628242aab341377be2f6670ca
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760253"
---
# <a name="compiler-error-c2687"></a>編譯器錯誤 C2687

' type '：例外狀況宣告不可以是 ' void '，或表示不完整的類型或不完整類型的指標或參考

若要讓類型成為例外狀況宣告的一部分，則必須定義，而不是 void。

下列範例會產生 C2687：

```cpp
// C2687.cpp
class C;

int main() {
   try {}
   catch (C) {}   // C2687 error
}
```

可能的解決方案：

```cpp
// C2687b.cpp
// compile with: /EHsc
class C {};

int main() {
   try {}
   catch (C) {}
}
```
