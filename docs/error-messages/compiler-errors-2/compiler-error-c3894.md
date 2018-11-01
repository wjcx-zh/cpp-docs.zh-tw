---
title: 編譯器錯誤 C3894
ms.date: 11/04/2016
f1_keywords:
- C3894
helpviewer_keywords:
- C3894
ms.assetid: 6d5ac903-1dea-431d-8e3a-cebca4342983
ms.openlocfilehash: 4d935e140d89cb5c3714450597677a7a02a245e8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50496040"
---
# <a name="compiler-error-c3894"></a>編譯器錯誤 C3894

'var': initonly 靜態資料成員的左值使用只允許在類別 'class' 的類別建構函式

靜態[initonly](../../dotnet/initonly-cpp-cli.md)資料成員只可用來當做左值在其宣告，或在靜態建構函式中的點。

執行個體 （非靜態） initonly 資料成員只可用來當做左值在其宣告，或執行個體 （非靜態） 建構函式中的點。

下列範例會產生 C3894:

```
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