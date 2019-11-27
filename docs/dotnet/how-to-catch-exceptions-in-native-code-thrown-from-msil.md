---
title: 如何：攔截 MSIL 擲回之機器碼的例外狀況
ms.date: 11/04/2016
helpviewer_keywords:
- exceptions, catching
- catching exceptions, thrown from MSIL
- MSIL, catching exceptions in native code
ms.assetid: c15afd2b-8505-43bf-8a4a-f1d41532a124
ms.openlocfilehash: c3afa29d8c9bee1c1f1cc2fd1869d108c08a249b
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246683"
---
# <a name="how-to-catch-exceptions-in-native-code-thrown-from-msil"></a>如何：攔截 MSIL 擲回之機器碼的例外狀況

在機器碼中，您可以從 MSIL C++攔截原生例外狀況。  您可以使用 `__try` 和 `__except`攔截 CLR 例外狀況。

如需詳細資訊，請參閱[結構化例外狀況C++處理（C/）](../cpp/structured-exception-handling-c-cpp.md)和[例外狀況和錯誤處理的現代化C++最佳作法](../cpp/errors-and-exception-handling-modern-cpp.md)。

## <a name="example"></a>範例

下列範例會定義具有兩個函式的模組，其中一個會擲回原生例外狀況，另一個則擲回 MSIL 例外狀況。

```
// catch_MSIL_in_native.cpp
// compile with: /clr /c
void Test() {
   throw ("error");
}

void Test2() {
   throw (gcnew System::Exception("error2"));
}
```

## <a name="example"></a>範例

下列範例會定義可攔截原生和 MSIL 例外狀況的模組。

```
// catch_MSIL_in_native_2.cpp
// compile with: /clr catch_MSIL_in_native.obj
#include <iostream>
using namespace std;
void Test();
void Test2();

void Func() {
   // catch any exception from MSIL
   // should not catch Visual C++ exceptions like this
   // runtime may not destroy the object thrown
   __try {
      Test2();
   }
   __except(1) {
      cout << "caught an exception" << endl;
   }

}

int main() {
   // catch native C++ exception from MSIL
   try {
      Test();
   }
   catch(char * S) {
      cout << S << endl;
   }
   Func();
}
```

```Output
error
caught an exception
```

## <a name="see-also"></a>另請參閱

[例外狀況處理](../extensions/exception-handling-cpp-component-extensions.md)
