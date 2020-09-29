---
title: 如何：使用 C++ Interop 封送處理 ANSI 字串
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], strings
- ANSI [C++], marshaling strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
ms.assetid: 5eda2eb6-5140-40f0-82cf-7ce171fffb45
ms.openlocfilehash: 3bdffa761bef74b9956842122b913e8213c736e9
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414564"
---
# <a name="how-to-marshal-ansi-strings-using-c-interop"></a>如何：使用 C++ Interop 封送處理 ANSI 字串

本主題將示範如何使用 c + + Interop 來傳遞 ANSI 字串，但 .NET Framework <xref:System.String> 代表 Unicode 格式的字串，因此轉換成 ANSI 是一個額外的步驟。 如需與其他字串類型交互操作，請參閱下列主題：

- [如何：使用 c + + Interop 封送處理 Unicode 字串](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)

- [如何：使用 c + + Interop 封送處理 COM 字串](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)

下列程式碼範例使用 [managed、非](../preprocessor/managed-unmanaged.md) 受控 #pragma 指示詞，在相同的檔案中執行 managed 和非受控函式，但這些函式在個別檔案中定義時，會以相同的方式相交互操作。 因為只包含非受控函式的檔案不需要使用 [/clr (Common Language Runtime 編譯) ](../build/reference/clr-common-language-runtime-compilation.md)來進行編譯，所以它們可以保留其效能特性。

## <a name="example-pass-ansi-string"></a>範例：傳遞 ANSI 字串

此範例示範如何使用，將來自 managed 的 ANSI 字串傳遞至非受控函數 <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> 。 這個方法會在非受控堆積上配置記憶體，並在執行轉換之後傳回位址。 這表示沒有必要的釘選 (因為 GC 堆積上的記憶體未傳遞至非受控函式) ，而且從傳回的 IntPtr <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> 必須明確釋放或記憶體流失結果。

```cpp
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

## <a name="example-data-marshaling-required-to-access-ansi-string"></a>範例：存取 ANSI 字串所需的資料封送處理

下列範例示範在非受控函式所呼叫的 managed 函式中存取 ANSI 字串所需的資料封送處理。 Managed 函式在接收原生字串時，可以直接使用它，或使用方法將它轉換成 managed 字串 <xref:System.Runtime.InteropServices.Marshal.PtrToStringAnsi%2A> ，如下所示。

```cpp
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

[使用 c + + Interop (隱含 PInvoke) ](../dotnet/using-cpp-interop-implicit-pinvoke.md)
