---
title: HOW TO：從 MSIL 擲回的原生程式碼中攔截例外狀況
ms.date: 11/04/2016
helpviewer_keywords:
- exceptions, catching
- catching exceptions, thrown from MSIL
- MSIL, catching exceptions in native code
ms.assetid: c15afd2b-8505-43bf-8a4a-f1d41532a124
ms.openlocfilehash: acb3ba1ab6d10decba10b899861007abfff03359
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57748719"
---
# <a name="how-to-catch-exceptions-in-native-code-thrown-from-msil"></a>HOW TO：從 MSIL 擲回的原生程式碼中攔截例外狀況

原生程式碼，您可以攔截從 MSIL 的原生 c + + 例外狀況。  您可以攔截與 CLR 例外狀況`__try`和`__except`。

如需詳細資訊，請參閱 < [Structured Exception Handling （C/c + +）](../cpp/structured-exception-handling-c-cpp.md)並[c + + 例外狀況處理](../cpp/cpp-exception-handling.md)。

## <a name="example"></a>範例

下列範例會定義具有兩個函式，其中一個原生的例外狀況，則會擲回，另一個會擲回例外狀況 MSIL 的模組。

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

下列範例會定義模組攔截原生和 MSIL 的例外狀況。

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

[例外狀況處理](../windows/exception-handling-cpp-component-extensions.md)
