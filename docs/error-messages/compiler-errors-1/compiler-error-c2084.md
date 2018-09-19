---
title: 編譯器錯誤 C2084 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2084
dev_langs:
- C++
helpviewer_keywords:
- C2084
ms.assetid: 990b107f-3721-4851-ae8b-4b69a8c149ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 09ce703b6908257e37c2b7ff1b2714f1426f941f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052103"
---
# <a name="compiler-error-c2084"></a>編譯器錯誤 C2084

函式 '*函式*' již obsahuje tělo

已定義的函式。

在 Visual Studio 2002 之前的 Visual c + + 的版本

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