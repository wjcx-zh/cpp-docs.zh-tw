---
title: 編譯器錯誤 C3215
ms.date: 11/04/2016
f1_keywords:
- C3215
helpviewer_keywords:
- C3215
ms.assetid: d0d16007-8885-42e0-b086-2d3a61f348c5
ms.openlocfilehash: b9a6d9cd57572f65b24656fa527725c9c605143d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50628263"
---
# <a name="compiler-error-c3215"></a>編譯器錯誤 C3215

'type1': 泛型類型參數已經受到 'type2' 的條件約束

條件約束指定了一次以上。

如需泛型的詳細資訊，請參閱 [Generics](../../windows/generics-cpp-component-extensions.md)。

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