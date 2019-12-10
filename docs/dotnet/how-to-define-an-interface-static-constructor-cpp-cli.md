---
title: 如何：定義介面靜態建構函式 (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- constructors [C++]
- static constructors, interface
- interface static constructor
ms.assetid: 1f031cb2-e94f-43dc-819b-44cf2faaaa49
ms.openlocfilehash: 562605a579ac372e4a69953853a6e32668357565
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988237"
---
# <a name="how-to-define-an-interface-static-constructor-ccli"></a>如何：定義介面靜態建構函式 (C++/CLI)

可具備靜態建構函式的介面，您可用它來初始化靜態資料成員。  靜態建構函式最多只能呼叫一次，而且會在第一次存取靜態介面成員之前呼叫。

## <a name="example"></a>範例

```cpp
// mcppv2_interface_class2.cpp
// compile with: /clr
using namespace System;

interface struct MyInterface {
   static int i;
   static void Test() {
      Console::WriteLine(i);
   }

   static MyInterface() {
      Console::WriteLine("in MyInterface static constructor");
      i = 99;
   }
};

ref class MyClass : public MyInterface {};

int main() {
   MyInterface::Test();
   MyClass::MyInterface::Test();

   MyInterface ^ mi = gcnew MyClass;
   mi->Test();
}
```

```Output
in MyInterface static constructor
99
99
99
```

## <a name="see-also"></a>請參閱

[介面類別](../extensions/interface-class-cpp-component-extensions.md)
