---
title: 編譯器錯誤 C2991
ms.date: 11/04/2016
f1_keywords:
- C2991
helpviewer_keywords:
- C2991
ms.assetid: a87e4404-26e8-4927-b3ee-5d02b3b8bee1
ms.openlocfilehash: bb7d709f757b6da10c8b17d5b30e2c2b86edd85e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366091"
---
# <a name="compiler-error-c2991"></a>編譯器錯誤 C2991

重複定義類型參數 'parameter'

`parameter`的兩個泛型或樣板定義之間發生類型衝突。 定義多個泛型或樣板參數時，您必須使用對等的類型。

下列範例會產生 C2991：

```
// C2991.cpp
// compile with: /c
template<class T, class T> struct TC {};   // C2991
// try the following line instead
// template<class T, class T2> struct TC {};
```

使用泛型時，也會發生 C2991：

```
// C2991b.cpp
// compile with: /clr /c
generic<class T,class T> ref struct GC {};   // C2991
// try the following line instead
// generic<class T,class T2> ref struct GC {};
```