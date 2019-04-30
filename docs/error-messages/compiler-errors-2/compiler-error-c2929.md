---
title: 編譯器錯誤 C2929
ms.date: 11/04/2016
f1_keywords:
- C2929
helpviewer_keywords:
- C2929
ms.assetid: 11134027-6adc-4733-b6bd-b94486bd1933
ms.openlocfilehash: fe2a56f7722c70c11e980fb6ee59230ffd056c5f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385715"
---
# <a name="compiler-error-c2929"></a>編譯器錯誤 C2929

'identifier': 明確具現化 (Explicit Instantiation); 無法強制地將樣板類別 (Template-Class) 成員具現化

您無法明確具現化識別項，同時又防止它具現化。

下列範例會產生 C2929：

```
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