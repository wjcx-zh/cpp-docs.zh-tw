---
title: 編譯器錯誤 C3160
ms.date: 11/04/2016
f1_keywords:
- C3160
helpviewer_keywords:
- C3160
ms.assetid: a250c433-8adf-43b9-8dee-c3794e09b0a5
ms.openlocfilehash: 96fd97aa5021b7e1bc5226162f9c54ff4d6211b1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62175222"
---
# <a name="compiler-error-c3160"></a>編譯器錯誤 C3160

'pointer': Managed 或 WinRT 類別的資料成員不能有這種類型

內部記憶體回收指標可能指向 Managed 或 WinRT 類別的內部。 因為它們比完整物件指標更慢，而且需要記憶體回收行程進行特殊處理，您無法將內部 Managed 指標宣告為類別的成員。

下列範例會產生 C3160：

```
// C3160.cpp
// compile with: /clr
ref struct A {
   // cannot create interior pointers inside a class
   interior_ptr<int> pg;   // C3160
   int g;   // OK
   int* pg2;   // OK
};

int main() {
   interior_ptr<int> pg2;   // OK
}
```
