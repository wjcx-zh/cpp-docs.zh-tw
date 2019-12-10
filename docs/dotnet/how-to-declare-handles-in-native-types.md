---
title: 如何：以原生類型宣告控制代碼
ms.custom: get-started-article
ms.date: 11/04/2016
f1_keywords:
- gcroot
helpviewer_keywords:
- handles, declaring
- gcroot keyword [C++]
- types [C++], declaring handles in
ms.assetid: b8c0eead-17e5-4003-b21f-b673f997d79f
ms.openlocfilehash: 11dbc196a89a224afe02312fbe4dff99d8467f4c
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988244"
---
# <a name="how-to-declare-handles-in-native-types"></a>如何：以原生類型宣告控制代碼

您不能在原生類型中宣告控制碼類型。 vcclr 提供型別安全的包裝函式範本，`gcroot` 從C++堆積參考 CLR 物件。 此範本可讓您將虛擬控制碼內嵌在原生類型中，並將它視為基礎類型。 在大部分的情況下，您可以使用 `gcroot` 物件做為內嵌類型，而不需要任何轉換。 不過，[針對每個，在中](../dotnet/for-each-in.md)，您必須使用 `static_cast` 來取得基礎的 managed 參考。

`gcroot` 範本是使用實值類別 System：： Runtime：： System.runtime.interopservices.outattribute：： GCHandle 的功能來實作為，它會在垃圾收集堆積中提供「控制碼」。 請注意，控制碼本身不會進行垃圾收集，並且會在 `gcroot` 類別中的析構函式不再使用時釋放（此析構函式無法以手動方式呼叫）。 如果您在原生堆積上具現化 `gcroot` 物件，您必須在該資源上呼叫 delete。

執行時間會維護控制碼和 CLR 物件之間的關聯，它會參考它。 當 CLR 物件與垃圾收集堆積一起移動時，控制碼會傳回物件的新位址。 變數在指派給 `gcroot` 範本之前，不需要固定。

## <a name="example"></a>範例

這個範例會示範如何在原生堆疊上建立 `gcroot` 物件。

```cpp
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

這個範例會示範如何在原生堆積上建立 `gcroot` 物件。

```cpp
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

這個範例會示範如何使用 `gcroot` 來保存原生類型中的實數值型別（不是參考型別）的參考，方法是使用已裝箱類型上的 `gcroot`。

```cpp
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

## <a name="see-also"></a>請參閱

[使用 C++ Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
