---
title: 編譯器錯誤 C3894
ms.date: 11/04/2016
f1_keywords:
- C3894
helpviewer_keywords:
- C3894
ms.assetid: 6d5ac903-1dea-431d-8e3a-cebca4342983
ms.openlocfilehash: c08a7eca473a4ae043879b49266efec6b8afe7b1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749434"
---
# <a name="compiler-error-c3894"></a>編譯器錯誤 C3894

' var '： initonly 靜態資料成員的左值使用只允許用於類別 ' class ' 的類別函式

靜態[initonly](../../dotnet/initonly-cpp-cli.md)資料成員只能在宣告的點或靜態的函式中當做左值使用。

實例（非靜態） initonly 資料成員只能用來做為宣告點的左值，或在實例（非靜態）的構造函式中。

下列範例會產生 C3894：

```cpp
// C3894.cpp
// compile with: /clr
ref struct Y1 {
   initonly static int data_var = 0;

public:
   // class constructor
   static Y1() {
      data_var = 99;   // OK
      System::Console::WriteLine("in static constructor");
   }

   // not the class constructor
   Y1(int i) {
      data_var = i;   // C3894
   }

   static void Test() {}

};

int main() {
   Y1::data_var = 88;   // C3894
   int i = Y1::data_var;
   Y1 ^ MyY1 = gcnew Y1(99);
   Y1::Test();
}
```
