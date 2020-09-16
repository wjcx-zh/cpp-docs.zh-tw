---
title: 如何：在-clr 編譯中使用原生類型
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- compilation, native types in /clr
- /clr compiler option [C++], using native types
ms.assetid: 3a505c90-4adb-4942-9cf9-7d1fdcbc01e7
ms.openlocfilehash: 88a678a19043d3229218dd69afbf8548348817df
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90683958"
---
# <a name="how-to-use-a-native-type-in-a-clr-compilation"></a>如何：在 /clr 編譯中使用原生類型

您可以在 **/clr** 編譯中定義原生類型，而且該原生類型在元件內的任何使用都是有效的。 不過，原生類型將無法從參考的中繼資料使用。

每個元件都必須包含它將使用的每個原生類型的定義。

如需詳細資訊，請參閱 [/clr (Common Language Runtime 編譯) ](../build/reference/clr-common-language-runtime-compilation.md)。

## <a name="examples"></a>範例

這個範例會建立定義和使用原生類型的元件。

```cpp
// use_native_type_in_clr.cpp
// compile with: /clr /LD
public struct NativeClass {
   static int Test() { return 98; }
};

public ref struct ManagedClass {
   static int i = NativeClass::Test();
   void Test() {
      System::Console::WriteLine(i);
   }
};
```

這個範例會定義使用元件的用戶端。 請注意，除非在編譯單位中定義，否則存取原生類型會是錯誤。

```cpp
// use_native_type_in_clr_2.cpp
// compile with: /clr
#using "use_native_type_in_clr.dll"
// Uncomment the following 3 lines to resolve.
// public struct NativeClass {
//    static int Test() { return 98; }
// };

int main() {
   ManagedClass x;
   x.Test();

   System::Console::WriteLine(NativeClass::Test());   // C2653
}
```

## <a name="see-also"></a>另請參閱

[使用 c + + Interop (隱含 PInvoke) ](../dotnet/using-cpp-interop-implicit-pinvoke.md)
