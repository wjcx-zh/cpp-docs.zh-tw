---
title: 編譯器錯誤 C2753
ms.date: 11/04/2016
f1_keywords:
- C2753
helpviewer_keywords:
- C2753
ms.assetid: 92bfeeac-524a-4a8e-9a4f-fb8269055826
ms.openlocfilehash: ea2901c998ac1a44ad142779e7ce48bfffff66c2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202143"
---
# <a name="compiler-error-c2753"></a>編譯器錯誤 C2753

'*template*'：部分特製化不能符合主要範本的引數清單

如果範本引數清單與參數清單相符，則編譯器會將它視為相同的範本。 不允許定義相同的範本兩次。

## <a name="example"></a>範例

下列範例會產生 C2753，並顯示可修正此問題的方法：

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
