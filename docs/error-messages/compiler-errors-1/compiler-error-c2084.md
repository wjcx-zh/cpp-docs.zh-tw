---
title: 編譯器錯誤 C2084
ms.date: 11/04/2016
f1_keywords:
- C2084
helpviewer_keywords:
- C2084
ms.assetid: 990b107f-3721-4851-ae8b-4b69a8c149ed
ms.openlocfilehash: 881ae051b2779fe674b31b64a7cbe7be7cf63705
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757887"
---
# <a name="compiler-error-c2084"></a>編譯器錯誤 C2084

函式 '*function*' 已經有主體

已經定義過函數。

Visual Studio 2002 之前，

- 編譯器會接受已解析成相同實際類型的多個樣板特製化，但不會有其他定義。 編譯器現在會偵測到這些多個定義。

- `__int32` 和 `int` 被視為不同的類型。 編譯器現在會將 `__int32` 視為 `int`的同義字。 這表示，如果在 `__int32` 和 `int` 上多載函式，而且發生錯誤，則編譯器會偵測多個定義。

## <a name="example"></a>範例

下列範例會產生 C2084：

```cpp
// C2084.cpp
void Func(int);
void Func(int) {}   // define function
void Func(int) {}   // C2084 second definition
```

若要更正此錯誤，請移除重複的定義：

```cpp
// C2084b.cpp
// compile with: /c
void Func(int);
void Func(int) {}
```
