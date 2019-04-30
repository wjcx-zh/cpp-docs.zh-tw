---
title: HOW TO：在-clr 編譯中使用原生類型
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- compilation, native types in /clr
- /clr compiler option [C++], using native types
ms.assetid: 3a505c90-4adb-4942-9cf9-7d1fdcbc01e7
ms.openlocfilehash: 9979113ac4ffc062ddfe8654279af03036984f38
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387197"
---
# <a name="how-to-use-a-native-type-in-a-clr-compilation"></a>HOW TO：在 /clr 編譯中使用原生類型

您可以定義中的原生型別 **/clr**編譯和任何使用組件中該原生類型無效。 不過，原生型別將無法供使用，從參考的中繼資料。

每個組件必須包含會使用每個原生類型的定義。

如需詳細資訊，請參閱 [/clr (Common Language Runtime 編譯)](../build/reference/clr-common-language-runtime-compilation.md)。

## <a name="example"></a>範例

此範例會建立定義，並使用原生類型的元件。

```
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

## <a name="example"></a>範例

這個範例會定義的用戶端所使用的元件。 請注意它是存取原生類型中，發生錯誤，除非它在編譯模組中定義。

```
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

[使用 C++ Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
