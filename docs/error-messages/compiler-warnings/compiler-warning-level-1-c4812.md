---
title: 編譯器警告 (層級 1) C4812
ms.date: 11/04/2016
f1_keywords:
- C4812
helpviewer_keywords:
- C4812
ms.assetid: a7f5721f-2019-44de-ad62-ed30bac8b1f3
ms.openlocfilehash: 6ba32bf3cad905d686eae78fbfbc198e911e91c8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406258"
---
# <a name="compiler-warning-level-1-c4812"></a>編譯器警告 (層級 1) C4812

過時的宣告樣式：請用 'new_syntax' 代替

在目前的 Visual C++ 版本中，仍然支援明確建構函式特製化，但未來的版本可能不予支援。

下列範例會產生 C4812：

```
// C4812.cpp
// compile with: /W1 /c
template <class T>
class MyClass;

template<class T>
class MyClass<T*> {
   MyClass();
};

template<class T>
MyClass<T*>::MyClass<T*>() {}   // C4812
// try the following line instead
// MyClass<T*>::MyClass() {}
```