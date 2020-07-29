---
title: 編譯器錯誤 C2084
ms.date: 11/04/2016
f1_keywords:
- C2084
helpviewer_keywords:
- C2084
ms.assetid: 990b107f-3721-4851-ae8b-4b69a8c149ed
ms.openlocfilehash: f217e0b94e27c0f85879e80b3ae887cb4f76f486
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216358"
---
# <a name="compiler-error-c2084"></a>編譯器錯誤 C2084

函式 '*function*' 已經有主體

已經定義過函數。

Visual Studio 2002 之前，

- 編譯器會接受已解析成相同實際類型的多個樣板特製化，但不會有其他定義。 編譯器現在會偵測到這些多個定義。

- **`__int32`** 和 **`int`** 被視為不同的類型。 編譯器現在會將視為 **`__int32`** 的同義字 **`int`** 。 這表示如果函式同時在和上超載，編譯器會偵測多個定義 **`__int32`** **`int`** ，並提供錯誤。

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
