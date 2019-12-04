---
title: 編譯器錯誤 C2815
ms.date: 11/04/2016
f1_keywords:
- C2815
helpviewer_keywords:
- C2815
ms.assetid: d0256fd6-0721-4c99-b03c-52d96e77a613
ms.openlocfilehash: 579fc94f3b16056b5f26dd0b9ea16b5fc36fda22
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750711"
---
# <a name="compiler-error-c2815"></a>編譯器錯誤 C2815

' operator delete '：第一個型式參數必須是 ' void * '，但使用了 ' param '

任何使用者定義的[運算子 delete](../../standard-library/new-operators.md#op_delete)函數都必須採用類型 `void *`的第一個型式參數。

下列範例會產生 C2815：

```cpp
// C2815.cpp
// compile with: /c
class CMyClass {
public:
   void mf1(int *a);
   void operator delete(CMyClass *);   // C2815
   void operator delete(void *);
};
```
