---
title: 如何： 攔截 MSIL 擲回之原生程式碼的例外狀況 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- exceptions, catching
- catching exceptions, thrown from MSIL
- MSIL, catching exceptions in native code
ms.assetid: c15afd2b-8505-43bf-8a4a-f1d41532a124
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f7022bffa7dd5a8524c614760fa2a36b2884b973
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46379459"
---
# <a name="how-to-catch-exceptions-in-native-code-thrown-from-msil"></a>如何：攔截 MSIL 擲回之機器碼的例外狀況

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