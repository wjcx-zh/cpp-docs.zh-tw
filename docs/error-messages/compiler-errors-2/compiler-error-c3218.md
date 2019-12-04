---
title: 編譯器錯誤 C3218
ms.date: 11/04/2016
f1_keywords:
- C3218
helpviewer_keywords:
- C3218
ms.assetid: 0eea19e0-503e-4e07-ae8b-2cb2e95922cd
ms.openlocfilehash: 386a0c180dd01161ebccdd2b04e899e0cc999614
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737981"
---
# <a name="compiler-error-c3218"></a>編譯器錯誤 C3218

' type '：類型不允許做為條件約束

若要讓類型成為條件約束，它必須是實數值型別或 managed 類別或介面的參考。

## <a name="example"></a>範例

下列範例會產生 C3218。

```cpp
// C3218.cpp
// compile with: /clr /c
class A {};
ref class B {};

// Delete the following 3 lines to resolve.
generic <class T>
where T : A   // C3218
ref class C {};

// OK
generic <class T>
where  T : B
ref class D {};
```
