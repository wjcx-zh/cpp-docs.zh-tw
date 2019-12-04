---
title: 編譯器錯誤 C2929
ms.date: 11/04/2016
f1_keywords:
- C2929
helpviewer_keywords:
- C2929
ms.assetid: 11134027-6adc-4733-b6bd-b94486bd1933
ms.openlocfilehash: d420e3f6470a94874549fadc8cd90e4dac20fe6e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760989"
---
# <a name="compiler-error-c2929"></a>編譯器錯誤 C2929

'identifier': 明確具現化 (Explicit Instantiation); 無法強制地將樣板類別 (Template-Class) 成員具現化

您無法明確具現化識別項，同時又防止它具現化。

下列範例會產生 C2929：

```cpp
// C2929.cpp
// compile with: /c
template<typename T>
class A {
public:
   A() {}
};

template A<int>::A();

extern template A<int>::A();   // C2929
```
