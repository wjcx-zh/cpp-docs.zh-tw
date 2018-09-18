---
title: 編譯器錯誤 C2753 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2753
dev_langs:
- C++
helpviewer_keywords:
- C2753
ms.assetid: 92bfeeac-524a-4a8e-9a4f-fb8269055826
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 722176744dc614e54d7b25ffd75be679ef9e63dc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46060579"
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