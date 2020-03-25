---
title: 編譯器錯誤 C3556
ms.date: 11/04/2016
f1_keywords:
- C3556
helpviewer_keywords:
- C3556
ms.assetid: 9b002dcc-494e-414f-9587-20c2a0a39333
ms.openlocfilehash: bc5eae58ac453182fd25853edd45e2c45093f5e5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200573"
---
# <a name="compiler-error-c3556"></a>編譯器錯誤 C3556

> '*expression*'： ' decltype ' 的引數不正確

編譯器無法減少 `decltype(`*expression*`)` 類型規範之引數的運算式類型。

## <a name="example"></a>範例

在下列程式碼範例中，編譯器無法減少 `myFunction` 引數的類型，因為 `myFunction` 多載。 若要修正這個問題，您可以使用 `static_cast` 建立特定多載函數指標的實例，以在 `decltype` 運算式中指定。

```cpp
// C3556.cpp
// compile with: cl /W4 /EHsc C3556.cpp
#include <iostream>

void myFunction(int);
void myFunction(float, float);

void callsMyFunction(decltype(myFunction) fn); // C3556
// One way to fix is to comment out the line above, and
// use static_cast to create specialized function pointer
// instances:
auto myFunctionInt = static_cast<void(*)(int)>(myFunction);
auto myFunctionFloatFloat = static_cast<void(*)(float,float)>(myFunction);
void callsMyFunction(decltype(myFunctionInt) fn, int n);
void callsMyFunction(decltype(myFunctionFloatFloat) fn, float f, float g);

void myFunction(int i) {
    std::cout << "called myFunction(" << i << ")" << std::endl;
}

void myFunction(float f, float g) {
    std::cout << "called myFunction(" << f << ", " << g << ")" << std::endl;
}

void callsMyFunction(decltype(myFunctionInt) fn, int n) {
    fn(n);
}

void callsMyFunction(decltype(myFunctionFloatFloat) fn, float f, float g) {
    fn(f, g);
}

int main() {
    callsMyFunction(myFunction, 42);
    callsMyFunction(myFunction, 0.1f, 2.3f);
}
```
