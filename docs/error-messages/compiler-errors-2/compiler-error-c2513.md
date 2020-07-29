---
title: 編譯器錯誤 C2513
ms.date: 11/04/2016
f1_keywords:
- C2513
helpviewer_keywords:
- C2513
ms.assetid: ab5b21d3-61e2-4df7-8eea-6f14d6ba8620
ms.openlocfilehash: 96f2ccc29eed5c1fa4e29f69d18ae6503417f211
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212718"
---
# <a name="compiler-error-c2513"></a>編譯器錯誤 C2513

' type '：未在 ' = ' 之前宣告任何變數

類型指定名稱會出現在宣告中，而且沒有任何變數識別碼。

下列範例會產生 C2513：

```cpp
// C2513.cpp
int main() {
   int = 9;   // C2513
   int i = 9;   // OK
}
```

針對 Visual Studio .NET 2003 執行的編譯器一致性工作，也可能會產生此錯誤：不再允許初始化 typedef。 標準不允許初始化 typedef，而且現在會產生編譯器錯誤。

```cpp
// C2513b.cpp
// compile with: /c
typedef struct S {
   int m_i;
} S = { 1 };   // C2513
// try the following line instead
// } S;
```

另一個方法是刪除 **`typedef`** 以定義具有匯總初始化運算式清單的變數，但不建議這樣做，因為它會建立與類型同名的變數，並隱藏類型名稱。
