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
ms.openlocfilehash: deba9804b9c5c278b3ffcef2923bc8f89fefa676
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684530"
---
# <a name="how-to-declare-handles-in-native-types"></a>如何：以原生類型宣告控制代碼

您無法以原生類型宣告控制碼類型。 vcclr 提供型別安全包裝函式範本 `gcroot` ，以從 c + + 堆積參考 CLR 物件。 此範本可讓您以原生類型內嵌虛擬控制碼，並將其視為基礎類型。 在大多數情況下，您可以使用 `gcroot` 物件做為內嵌類型，而不需要任何轉換。 不過， [在中](../dotnet/for-each-in.md)，您必須使用 **`static_cast`** 來取得基礎 managed 參考。

此 `gcroot` 範本會使用實值類別 System：： Runtime：： system.runtime.interopservices.outattribute：： GCHandle 的功能來執行，這會將「控制碼」提供給垃圾收集的堆積。 請注意，處理常式本身不會進行垃圾收集，而且當類別中的函式不再使用時，會釋出 `gcroot` (無法以手動方式呼叫這個函式) 。 如果您在 `gcroot` 原生堆積上具現化物件，您必須在該資源上呼叫 delete。

執行時間會維護控制碼和 CLR 物件（其參考）之間的關聯。 當 CLR 物件與垃圾收集堆積一起移動時，控制碼會傳回物件的新位址。 變數在指派給範本之前，不需要先釘選 `gcroot` 。

## <a name="examples"></a>範例

此範例說明如何 `gcroot` 在原生堆疊上建立物件。

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

此範例顯示如何 `gcroot` 在原生堆積上建立物件。

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

這個範例會示範如何使用 `gcroot` 來保存實值型別的參考， (不會使用在已裝箱的型別上) 于原生類型中的參考型別 `gcroot` 。

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

[使用 c + + Interop (隱含 PInvoke) ](../dotnet/using-cpp-interop-implicit-pinvoke.md)
