---
title: 如何： 在-clr 編譯中使用原生型別 |Microsoft Docs
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- compilation, native types in /clr
- /clr compiler option [C++], using native types
ms.assetid: 3a505c90-4adb-4942-9cf9-7d1fdcbc01e7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3e56c3617b6b2a8168e35867c09858dffa84cea9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46448060"
---
# <a name="how-to-use-a-native-type-in-a-clr-compilation"></a>如何：在 /clr 編譯中使用原生類型

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