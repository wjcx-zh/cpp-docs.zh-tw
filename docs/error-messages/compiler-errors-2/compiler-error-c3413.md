---
title: 編譯器錯誤 C3413
ms.date: 11/04/2016
f1_keywords:
- C3413
helpviewer_keywords:
- C3413
ms.assetid: de6c9b05-c373-4bd8-8cb0-12c2cd2e5674
ms.openlocfilehash: e344d06345c0f3a79b86e9cab4e1c5dacb47e9c2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62173420"
---
# <a name="compiler-error-c3413"></a>編譯器錯誤 C3413

'name': 無效的明確具現化

編譯器偵測到格式不正確的明確具現化。

下列範例會產生 C3413：

```
// C3413.cpp
template
class MyClass {};   // C3413
```

可能的解決方式：

```
// C3413b.cpp
// compile with: /c
template <class T>
class MyClass {};

template <>
class MyClass<int> {};
```