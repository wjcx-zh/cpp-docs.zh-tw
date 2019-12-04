---
title: 編譯器錯誤 C2943
ms.date: 11/04/2016
f1_keywords:
- C2943
helpviewer_keywords:
- C2943
ms.assetid: ede6565e-d892-44c0-8eee-c69545f3be2e
ms.openlocfilehash: ac704c06ac0e455cccdb2b035d0947ae9ec04bd5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755391"
---
# <a name="compiler-error-c2943"></a>編譯器錯誤 C2943

'class': type-class-id 重複定義為樣板的類型引數

您無法使用泛型或樣板類別取代符號作為泛型或樣板類型引數。

下列範例會產生 C2943：

```cpp
// C2943.cpp
// compile with: /c
template<class T>
class List {};

template<class List<int> > class MyList;   // C2943
template<class T >  class MyList;
```
