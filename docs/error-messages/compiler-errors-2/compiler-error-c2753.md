---
title: 編譯器錯誤 C2753
ms.date: 11/04/2016
f1_keywords:
- C2753
helpviewer_keywords:
- C2753
ms.assetid: 92bfeeac-524a-4a8e-9a4f-fb8269055826
ms.openlocfilehash: e13c45cec99e60d8aec7dcc3db8e5a4813ea7de9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62228779"
---
# <a name="compiler-error-c2753"></a>編譯器錯誤 C2753

'*範本*': 部分特製化不能符合主要樣板的引數清單

如果樣板引數清單符合在參數清單，則編譯器會將其視為相同的範本。 不允許兩次定義相同的範本。

## <a name="example"></a>範例

下列範例會產生 C2753，並示範如何修正此問題：

```cpp
// C2753.cpp
// compile with: cl /c C2753.cpp
template<class T>
struct A {};

template<class T>
struct A<T> {};   // C2753
// try the following line instead
// struct A<int> {};

template<class T, class U, class V, class W, class X>
struct B {};
```