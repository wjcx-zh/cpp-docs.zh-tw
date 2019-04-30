---
title: 編譯器錯誤 C2084
ms.date: 11/04/2016
f1_keywords:
- C2084
helpviewer_keywords:
- C2084
ms.assetid: 990b107f-3721-4851-ae8b-4b69a8c149ed
ms.openlocfilehash: 9aaf3a88e63234dfb842e4b48afd6e55595e96ca
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391916"
---
# <a name="compiler-error-c2084"></a>編譯器錯誤 C2084

函式 '*函式*' již obsahuje tělo

已定義的函式。

在 視覺效果的版本C++Visual Studio 2002 之前

- 雖然其他定義永遠無法使用，編譯器會接受解析為相同的實際類型的多個樣板特製化。 編譯器現在會偵測這些定義。

- `__int32` 和`int`被視為不同的類型。 編譯器現在會將`__int32`的同義字`int`。 這表示，編譯器偵測到多個定義如果函式多載上同時`__int32`和`int`而且會產生錯誤。

## <a name="example"></a>範例

下列範例會產生 C2084:

```cpp
// C2084.cpp
void Func(int);
void Func(int) {}   // define function
void Func(int) {}   // C2084 second definition
```

若要更正這個錯誤，請移除重複的定義：

```
// C2084b.cpp
// compile with: /c
void Func(int);
void Func(int) {}
```