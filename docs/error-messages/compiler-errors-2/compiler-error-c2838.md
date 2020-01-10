---
title: 編譯器錯誤 C2838
ms.date: 11/04/2016
f1_keywords:
- C2838
helpviewer_keywords:
- C2838
ms.assetid: 176b2ad6-7a84-4019-b97e-328866054457
ms.openlocfilehash: 168f45a8cca8591d4780d056403de70440d25bec
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757835"
---
# <a name="compiler-error-c2838"></a>編譯器錯誤 C2838

' member '：成員宣告中有不合法的限定名稱

類別、結構或聯集會使用完整名稱來重新宣告另一個類別、結構或等位的成員。

下列範例會產生 C2838：

```cpp
// C2838.cpp
// compile with: /c
class Bellini {
public:
    void Norma();
};

class Bottesini {
   Bellini::Norma();  // C2838
};
```
