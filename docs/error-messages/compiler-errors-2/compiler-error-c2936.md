---
title: 編譯器錯誤 C2936
ms.date: 11/04/2016
f1_keywords:
- C2936
helpviewer_keywords:
- C2936
ms.assetid: 5d1ba0fc-0c78-4a37-a83b-1ef8527763be
ms.openlocfilehash: d73f45440cf373368b70a11a7779f43587e73aca
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754650"
---
# <a name="compiler-error-c2936"></a>編譯器錯誤 C2936

'class' : type-class-id 重複定義為全域資料變數

您無法將泛型或範本類別用作為全域資料變數。

此錯誤可能是大括弧不對稱所造成。

下列範例會產生 C2936：

```cpp
// C2936.cpp
// compile with: /c
template<class T> struct TC { };
int TC<int>;   // C2936

// OK
struct TC2 { };
int TC2;
```

使用泛型時，也會發生 C2936：

```cpp
// C2936b.cpp
// compile with: /clr /c
generic<class T>
ref struct GC {};
int GC<int>;   // C2936

// OK
ref struct GC2 {};
int GC2;
```
