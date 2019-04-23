---
title: 編譯器錯誤 C3215
ms.date: 11/04/2016
f1_keywords:
- C3215
helpviewer_keywords:
- C3215
ms.assetid: d0d16007-8885-42e0-b086-2d3a61f348c5
ms.openlocfilehash: 24f17d2990c9258168a6d37fef101c21f62cb08d
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59778718"
---
# <a name="compiler-error-c3215"></a>編譯器錯誤 C3215

'type1': 泛型類型參數已經受到 'type2' 的條件約束

條件約束指定了一次以上。

如需泛型的詳細資訊，請參閱 [Generics](../../extensions/generics-cpp-component-extensions.md)。

下列範例會產生 C3215：

```
// C3215.cpp
// compile with: /clr
interface struct A {};

generic <class T>
where T : A,A
ref class C {};   // C3215
```

可能的解決方式：

```
// C3215b.cpp
// compile with: /clr /c
interface struct A {};

generic <class T>
where T : A
ref class C {};
```