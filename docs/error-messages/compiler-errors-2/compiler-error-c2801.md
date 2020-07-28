---
title: 編譯器錯誤 C2801
ms.date: 11/04/2016
f1_keywords:
- C2801
helpviewer_keywords:
- C2801
ms.assetid: 35dfc7ea-9e37-4e30-baa1-944dc61302f5
ms.openlocfilehash: cfb89c79534318ab1fbcaa06667d594bfe2f1157
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214590"
---
# <a name="compiler-error-c2801"></a>編譯器錯誤 C2801

' operator operator ' 必須是非靜態成員

下列運算子只能多載為非靜態成員：

- 指派`=`

- 類別成員存取`->`

- 注標`[]`

- 函式呼叫`()`

可能的 C2801 原因：

- 多載運算子不是類別、結構或等位成員。

- 已宣告多載的運算子 **`static`** 。

- 下列範例會產生 C2801：

```cpp
// C2801.cpp
// compile with: /c
operator[]();   // C2801 not a member
class A {
   static operator->();   // C2801 static
   operator()();   // OK
};
```
