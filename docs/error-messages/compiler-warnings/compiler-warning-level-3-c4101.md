---
title: 編譯器警告（層級3） C4101
ms.date: 11/04/2016
f1_keywords:
- C4101
helpviewer_keywords:
- C4101
ms.assetid: d98563cd-9dce-4aae-8f12-bd552a4ea677
ms.openlocfilehash: 5effdbb4c7e83999655641a248c389c7c4d260d0
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051909"
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

不過，透過類別的實例呼叫**靜態**成員函式時，也會發生這個警告：

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

在此情況下，編譯器會使用 `si` 的相關資訊來存取**靜態**函式，但不需要類別的實例來呼叫**靜態**函式;因此會出現警告。 若要解決這個警告，您可以：

- 加入一個處理函式，編譯器會在呼叫中使用 `si` 的實例 `func`。

- 從 `func`的定義中移除**static**關鍵字。

- 明確呼叫**靜態**函式： `int y = S::func();`。