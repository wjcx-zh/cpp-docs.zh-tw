---
title: 編譯器警告（層級3） C4101
ms.date: 11/04/2016
f1_keywords:
- C4101
helpviewer_keywords:
- C4101
ms.assetid: d98563cd-9dce-4aae-8f12-bd552a4ea677
ms.openlocfilehash: f9d3875fdc17def1e7d3bcb72149c5faf90f656a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220050"
---
# <a name="compiler-warning-level-3-c4101"></a>編譯器警告（層級3） C4101

' identifier '：未參考的區域變數

永遠不會使用本機變數。 此警告會在明顯的情況下發生：

```cpp
// C4101a.cpp
// compile with: /W3
int main() {
int i;   // C4101
}
```

不過，透過類別的實例呼叫成員函式時，也會發生這個警告 **`static`** ：

```cpp
// C4101b.cpp
// compile with:  /W3
struct S {
   static int func()
   {
      return 1;
   }
};

int main() {
   S si;   // C4101, si is never used
   int y = si.func();
   return y;
}
```

在此情況下，編譯器會使用的相關資訊 `si` 來存取函式 **`static`** ，但不需要類別的實例來呼叫函式， **`static`** 因此會出現警告。 若要解決這個警告，您可以：

- 加入一個函式，在其中，編譯器會 `si` 在的呼叫中使用的實例 `func` 。

- 請 **`static`** 從的定義中移除關鍵字 `func` 。

- 明確呼叫 **`static`** 函式： `int y = S::func();` 。
