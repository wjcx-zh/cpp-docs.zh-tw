---
title: 編譯器錯誤 C2577
ms.date: 11/04/2016
f1_keywords:
- C2577
helpviewer_keywords:
- C2577
ms.assetid: fc79ef83-8362-40a2-9257-8037c3195ce4
ms.openlocfilehash: acb42f9b792b3908a153737bcec93a449b656147
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755443"
---
# <a name="compiler-error-c2577"></a>編譯器錯誤 C2577

' member '：析構函式/完成項不能有傳回類型

「析構器」或「完成項」無法傳回 `void` 或任何其他類型的值。 請從析構函式定義中移除 `return` 語句。

## <a name="example"></a>範例

下列範例會產生 C2577。

```cpp
// C2577.cpp
// compile with: /c
class A {
public:
   A() {}
   ~A(){
      return 0;   // C2577
   }
};
```
