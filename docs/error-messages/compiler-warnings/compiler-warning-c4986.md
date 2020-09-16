---
title: 編譯器警告 C4986
ms.date: 11/04/2016
f1_keywords:
- C4986
helpviewer_keywords:
- C4986
ms.assetid: a3a7b008-29dd-4203-85f3-7740ab6790bb
ms.openlocfilehash: ae782ea0a11bd72c867ea9532a62d0b14cd98453
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684388"
---
# <a name="compiler-warning-c4986"></a>編譯器警告 C4986

'function'：例外狀況規格與上一個宣告不符

當一個宣告中有例外狀況規格，而另一個宣告沒有時，可能會產生這項警告。

C4986 預設為關閉。 如需詳細資訊，請參閱 [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。

## <a name="examples"></a>範例

下列範例會產生 C4986。

```cpp
class X { };
void f1() throw (X*);
// ...
void f1()
{
    // ...
}
```

下列範例程式碼會消除這則警告。

```cpp
class X { };
void f1() throw (X*);
// ...
void f1() throw (X*)
{
    // ...
}
```
