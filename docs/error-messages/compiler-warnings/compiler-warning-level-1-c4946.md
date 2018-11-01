---
title: 編譯器警告 (層級 1) C4946
ms.date: 11/04/2016
f1_keywords:
- C4946
helpviewer_keywords:
- C4946
ms.assetid: b85cbef0-e053-4de6-9b14-7b0f82d40495
ms.openlocfilehash: f215c621486bf223d8f6c90b0a4f4ae119ad4b1f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50574222"
---
# <a name="compiler-warning-level-1-c4946"></a>編譯器警告 (層級 1) C4946

在關聯的類別之間使用的 reinterpret_cast：'class1' 和 'class2'

請勿使用[reinterpret_cast](../../cpp/reinterpret-cast-operator.md)相關的類型之間轉換。 使用  [static_cast](../../cpp/static-cast-operator.md)相反的或針對多型類型，使用[dynamic_cast](../../cpp/dynamic-cast-operator.md)。

根據預設，此警告為關閉。 如需詳細資訊，請參閱 [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。

下列程式碼範例會產生 C4946：

```
// C4946.cpp
// compile with: /W1
#pragma warning (default : 4946)
class a {
public:
   a() : m(0) {}
   int m;
};

class b : public virtual a {
};

class b2 : public virtual a {
};

class c : public b, public b2 {
};

int main() {
   c* pC = new c;
   a* pA = reinterpret_cast<a*>(pC);   // C4946
   // try the following line instead
   // a* pA = static_cast<a*>(pC);
}
```