---
title: 編譯器錯誤 C3413
ms.date: 11/04/2016
f1_keywords:
- C3413
helpviewer_keywords:
- C3413
ms.assetid: de6c9b05-c373-4bd8-8cb0-12c2cd2e5674
ms.openlocfilehash: 3065478cfff51f2463d4efba7f5a7dafc482fa65
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743012"
---
# <a name="compiler-error-c3413"></a>編譯器錯誤 C3413

'name': 無效的明確具現化

編譯器偵測到格式不正確的明確具現化。

下列範例會產生 C3413：

```cpp
// C3413.cpp
template
class MyClass {};   // C3413
```

可能的解決方案：

```cpp
// C3413b.cpp
// compile with: /c
template <class T>
class MyClass {};

template <>
class MyClass<int> {};
```
