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
ms.openlocfilehash: 1aca21402122a0c8641a7e57ace2a3477ff96f01
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221337"
---
# <a name="how-to-declare-handles-in-native-types"></a>如何：以原生類型宣告控制代碼

您不能在原生類型中宣告控制碼類型。 vcclr 提供型別安全包裝函式範本 `gcroot` ，以從 c + + 堆積參考 CLR 物件。 此範本可讓您將虛擬控制碼內嵌在原生類型中，並將它視為基礎類型。 在大部分的情況下，您可以使用 `gcroot` 物件做為內嵌類型，而不需要任何轉換。 不過，[針對每個，在中](../dotnet/for-each-in.md)，您必須使用 **`static_cast`** 來取出基礎 managed 參考。

此 `gcroot` 範本是使用實值類別 System：： Runtime：： system.runtime.interopservices.outattribute：： GCHandle 的功能來實作為，它會在垃圾收集堆積中提供「控制碼」。 請注意，控制碼本身不會進行垃圾收集，並且會在類別中的析構函式不再使用時釋放 `gcroot` （無法手動呼叫此析構函式）。 如果您在 `gcroot` 原生堆積上具現化物件，您必須在該資源上呼叫 delete。

執行時間會維護控制碼和 CLR 物件之間的關聯，它會參考它。 當 CLR 物件與垃圾收集堆積一起移動時，控制碼會傳回物件的新位址。 變數在指派給範本之前，不需要固定 `gcroot` 。

## <a name="example"></a>範例

這個範例會顯示如何 `gcroot` 在原生堆疊上建立物件。

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

這個範例會顯示如何 `gcroot` 在原生堆積上建立物件。

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

這個範例示範如何使用，在已 `gcroot` 裝箱的類型上使用來保存原生類型中的實數值型別（不是參考型別）的參考 `gcroot` 。

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

## <a name="see-also"></a>另請參閱

[使用 c + + Interop （隱含 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)
