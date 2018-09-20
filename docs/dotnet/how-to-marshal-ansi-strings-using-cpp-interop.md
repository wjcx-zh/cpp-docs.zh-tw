---
title: 如何： 使用 c + + Interop 封送處理 ANSI 字串 |Microsoft Docs
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interop [C++], strings
- ANSI [C++], marshaling strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
ms.assetid: 5eda2eb6-5140-40f0-82cf-7ce171fffb45
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d4a1a0cd8b9da5812e404f70dc999dfaf1606666
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46383359"
---
# <a name="how-to-marshal-ansi-strings-using-c-interop"></a>如何：使用 C++ Interop 封送處理 ANSI 字串

本主題示範的 ANSI 字串可以是如何使用 c + + 互通性之外，但.NET Framework 傳遞<xref:System.String>代表以 Unicode 格式的字串，因此轉換成 ANSI 是額外的步驟。 與其他字串類型的交互操作，請參閱下列主題：

- [如何：使用 C++ Interop 封送處理 Unicode 字串](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)

- [如何：使用 C++ Interop 封送處理 COM 字串](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)

下列程式碼範例使用[managed、 unmanaged](../preprocessor/managed-unmanaged.md) #pragma 指示詞來實作 managed 和 unmanaged 函式在相同的檔案，但如果在不同的檔案中定義這些函式交互操作方式相同。 因為檔案包含 unmanaged 的函式不需要編譯[/clr （Common Language Runtime 編譯）](../build/reference/clr-common-language-runtime-compilation.md)，它們可以保留其效能特性。

## <a name="example"></a>範例

此範例會示範從 managed 的 ANSI 字串傳遞至 unmanaged 函式使用<xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A>。 這個方法會針對未受管理的堆積配置記憶體，並將位址傳回之後執行轉換。 這表示未釘選的必要 （因為在 GC 堆積上的記憶體不會傳遞至 unmanaged 函式），並從傳回的 IntPtr<xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A>必須明確釋放或記憶體流失的結果。

```
// MarshalANSI1.cpp
// compile with: /clr
#include <iostream>
#include <stdio.h>

using namespace std;
using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

void NativeTakesAString(const char* p) {
   printf_s("(native) received '%s'\n", p);
}

#pragma managed

int main() {
   String^ s = gcnew String("sample string");
   IntPtr ip = Marshal::StringToHGlobalAnsi(s);
   const char* str = static_cast<const char*>(ip.ToPointer());

   Console::WriteLine("(managed) passing string...");
   NativeTakesAString( str );

   Marshal::FreeHGlobal( ip );
}
```

## <a name="example"></a>範例

下列範例示範資料封送處理，才能存取 unmanaged 函式會呼叫 managed 函式中的 ANSI 字串。 受管理的函式，在接收的原生的字串，可以直接使用它或將它轉換成 managed 的字串，使用<xref:System.Runtime.InteropServices.Marshal.PtrToStringAnsi%2A>方法，如所示。

```
// MarshalANSI2.cpp
// compile with: /clr
#include <iostream>
#include <vcclr.h>

using namespace std;

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma managed

void ManagedStringFunc(char* s) {
   String^ ms = Marshal::PtrToStringAnsi(static_cast<IntPtr>(s));
   Console::WriteLine("(managed): received '{0}'", ms);
}

#pragma unmanaged

void NativeProvidesAString() {
   cout << "(native) calling managed func...\n";
   ManagedStringFunc("test string");
}

#pragma managed

int main() {
   NativeProvidesAString();
}
```

## <a name="see-also"></a>另請參閱

[使用 C++ Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)