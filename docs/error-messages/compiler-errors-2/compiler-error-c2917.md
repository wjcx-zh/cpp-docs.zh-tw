---
title: 編譯器錯誤 C2917
ms.date: 11/04/2016
f1_keywords:
- C2917
helpviewer_keywords:
- C2917
ms.assetid: ec9da9ee-0f37-47b3-87dd-19ef5a14dc4c
ms.openlocfilehash: 9f4b82c1138326bad93d3836d6a77c55f2f546e4
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761041"
---
# <a name="compiler-error-c2917"></a>編譯器錯誤 C2917

'name': 無效的樣板-參數

樣板參數清單包含不是樣板參數的識別項。

## <a name="example"></a>範例

下列範例會產生 C2917：

```cpp
// C2917.cpp
// compile with: /c
template<class T> class Vector {
   void sort();
};

template<class T*> void Vector<T>::sort() {}   // C2917
// try the following line instead
// template<class T> void Vector<T>::sort() {}
```
