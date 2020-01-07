---
title: 編譯器錯誤 C2085
ms.date: 11/04/2016
f1_keywords:
- C2085
helpviewer_keywords:
- C2085
ms.assetid: 0a86785c-8e6f-481b-8c7b-412220c1950d
ms.openlocfilehash: 7dbf7266a6330a1fdb46d7f2df90e7684f026d9a
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301960"
---
# <a name="compiler-error-c2085"></a>編譯器錯誤 C2085

' identifier '：不在型式參數清單中

識別碼是在函式定義中宣告，而不是在型式參數清單中宣告。 （僅限 ANSI C）

下列範例會產生 C2085：

```c
// C2085.c
void func1( void )
int main( void ) {}   // C2085
```

可能的解決方案：

```c
// C2085b.c
void func1( void );
int main( void ) {}
```

如果遺漏分號，`func1()` 看起來就像函式定義，而不是原型，因此 `main` 定義在 `func1()`內，產生識別碼 `main`的錯誤 C2085。
