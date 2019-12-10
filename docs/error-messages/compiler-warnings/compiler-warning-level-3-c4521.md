---
title: 編譯器警告 (層級 3) C4521
ms.date: 11/04/2016
f1_keywords:
- C4521
helpviewer_keywords:
- C4521
ms.assetid: 057d770c-ebcf-44cd-b943-1b1bb1ceaa8c
ms.openlocfilehash: 79e0866262b2db18424355de0702288d0f24592d
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74992072"
---
# <a name="compiler-warning-level-3-c4521"></a>編譯器警告 (層級 3) C4521

' class '：指定了多個複製的構造函式

類別具有單一類型的多個複製函數。 此警告僅供參考。在您的程式中可以呼叫這些函式。

請使用[warning](../../preprocessor/warning.md) pragma 來隱藏這個警告。

## <a name="example"></a>範例

下列範例會產生 C4521。

```cpp
// C4521.cpp
// compile with: /EHsc /W3
#include <iostream>

using namespace std;
class A {
public:
   A() { cout << "A's default constructor" << endl; }
   A( A &o ) { cout << "A&" << endl; }
   A( const A &co ) { cout << "const A&" << endl; }   // C4521
};

int main() {
   A o1;         // Calls default constructor.
   A o2( o1 );   // Calls A( A& ).
   const A o3;   // Calls default constructor.
   A o4( o3 );   // Calls A( const A& ).
}
```
