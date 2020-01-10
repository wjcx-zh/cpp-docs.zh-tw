---
title: 編譯器錯誤 C2228
ms.date: 11/04/2016
f1_keywords:
- C2228
helpviewer_keywords:
- C2228
ms.assetid: 901cadb1-ce90-4ae0-a360-547a9ba2ca18
ms.openlocfilehash: 56eed6aeff5a955253a440d5931d66118f4604e0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759278"
---
# <a name="compiler-error-c2228"></a>編譯器錯誤 C2228

'.identifier' 的左邊必須有類別/結構/等位

句點（.）左邊的運算元不是類別、結構或等位。

下列範例會產生 C2228：

```cpp
// C2228.cpp
int i;
struct S {
public:
    int member;
} s, *ps = &s;

int main() {
   i.member = 0;   // C2228 i is not a class type
   ps.member = 0;  // C2228 ps is a pointer to a structure

   s.member = 0;   // s is a structure type
   ps->member = 0; // ps points to a structure S
}
```

如果使用 Managed Extensions 時用了不正確的語法，您也會看到這個錯誤。 至於其他 Visual Studio 語言，您可以使用點運算子來存取 Managed 類別的成員，C++ 中的物件指標表示您必須使用 -> 運算子來存取成員：

錯誤： `String * myString = checkedListBox1->CheckedItems->Item[0].ToString();`

正確： `String * myString = checkedListBox1->CheckedItems->Item[0]->ToString();`
