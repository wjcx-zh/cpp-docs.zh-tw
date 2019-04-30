---
title: HOW TO：以原生類型宣告控制代碼
ms.custom: get-started-article
ms.date: 11/04/2016
f1_keywords:
- gcroot
helpviewer_keywords:
- handles, declaring
- gcroot keyword [C++]
- types [C++], declaring handles in
ms.assetid: b8c0eead-17e5-4003-b21f-b673f997d79f
ms.openlocfilehash: f5d6d31be9f3c10e1a56639ccf20663ce59d7941
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387405"
---
# <a name="how-to-declare-handles-in-native-types"></a>HOW TO：以原生類型宣告控制代碼

您無法宣告原生類型中的控制代碼型別。 vcclr.h 提供型別安全包裝函式樣板`gcroot`參考的 CLR 物件，從C++堆積。 此範本可讓您在原生類型中嵌入虛擬控制代碼，並將它視為基礎型別。 在大部分情況下，您可以使用`gcroot`物件做為內嵌的型別，而不需要任何轉換。 不過，透過[針對每個，在](../dotnet/for-each-in.md)，您必須使用`static_cast`擷取基礎受管理的參考。

`gcroot`範本實作到記憶體回收堆積中使用的實值類別 System::Runtime::InteropServices::GCHandle，提供 「 handles 」 功能。 請注意，本身的控點無法回收，並釋放時不再使用中的解構函式中`gcroot`類別 （此解構函式無法呼叫手動）。 如果您具現化`gcroot`物件上原生堆積中，您必須呼叫刪除該資源上。

執行階段會維持控制代碼所參考的 CLR 物件之間的關聯。 當 CLR 物件會隨之移動記憶體回收堆積時，控制代碼會傳回物件的新位址。 變數不必先將它指派給釘選`gcroot`範本。

## <a name="example"></a>範例

此範例示範如何建立`gcroot`原生堆疊上的物件。

```
// mcpp_gcroot.cpp
// compile with: /clr
#include <vcclr.h>
using namespace System;

class CppClass {
public:
   gcroot<String^> str;   // can use str as if it were String^
   CppClass() {}
};

int main() {
   CppClass c;
   c.str = gcnew String("hello");
   Console::WriteLine( c.str );   // no cast required
}
```

```Output
hello
```

## <a name="example"></a>範例

此範例示範如何建立`gcroot`原生堆積上的物件。

```
// mcpp_gcroot_2.cpp
// compile with: /clr
// compile with: /clr
#include <vcclr.h>
using namespace System;

struct CppClass {
   gcroot<String ^> * str;
   CppClass() : str(new gcroot<String ^>) {}

   ~CppClass() { delete str; }

};

int main() {
   CppClass c;
   *c.str = gcnew String("hello");
   Console::WriteLine( *c.str );
}
```

```Output
hello
```

## <a name="example"></a>範例

此範例示範如何使用`gcroot`保留在原生類型中的實值型別 （不是參考型別） 的參考，藉由使用`gcroot`boxed 型別上。

```
// mcpp_gcroot_3.cpp
// compile with: /clr
#include < vcclr.h >
using namespace System;

public value struct V {
   String^ str;
};

class Native {
public:
   gcroot< V^ > v_handle;
};

int main() {
   Native native;
   V v;
   native.v_handle = v;
   native.v_handle->str = "Hello";
   Console::WriteLine("String in V: {0}", native.v_handle->str);
}
```

```Output
String in V: Hello
```

## <a name="see-also"></a>另請參閱

[使用 C++ Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
