---
title: 編譯器錯誤 C2062
ms.date: 11/04/2016
f1_keywords:
- C2062
helpviewer_keywords:
- C2062
ms.assetid: 6cc98353-2ddf-43ab-88a2-9cc91cdd6033
ms.openlocfilehash: a709a540b24756a7e08f98552c5888a55c3ea601
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74735966"
---
# <a name="compiler-error-c2062"></a>編譯器錯誤 C2062

類型 ' type ' 未預期

編譯器不需要類型名稱。

下列範例會產生 C2062：

```cpp
// C2062.cpp
// compile with: /c
struct A {  : int l; };   // C2062
struct B { private: int l; };   // OK
```

C2062 也可能會因為編譯器在函式的參數清單中處理未定義的型別而發生。 如果編譯器遇到未定義（拼錯的？）型別，則會假設此函式為運算式，併發出 C2062。 若要解決此問題，請只在函式參數清單中使用已定義的類型。
