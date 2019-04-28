---
title: 編譯器錯誤 C2951
ms.date: 11/04/2016
f1_keywords:
- C2951
helpviewer_keywords:
- C2951
ms.assetid: c6f95aa2-c894-425b-a51c-d40d70c8daa1
ms.openlocfilehash: dbc7186edfce6cc12a38fb2fc1dda08ac4a181c7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62300722"
---
# <a name="compiler-error-c2951"></a>編譯器錯誤 C2951

類型宣告只允許在全域命名空間或類別範圍

您無法宣告泛型或樣板類別外全域或命名空間範圍。 如果您將泛型或樣板的宣告在 include 檔時，請確定包含檔案位於全域範圍。

下列範例會產生 C2951:

```
// C2951.cpp
template <class T>
class A {};

int main() {
   template <class T>   // C2951
   class B {};
}
```

使用泛型時，也會發生 C2951:

```
// C2951b.cpp
// compile with: /clr /c

// OK
generic <class T>
ref class GC { };

int main() {
   generic <class T> ref class GC2 {};   // C2951
}
```