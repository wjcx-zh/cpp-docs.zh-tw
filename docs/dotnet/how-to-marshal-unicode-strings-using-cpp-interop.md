---
title: 如何：使用 C++ Interop 封送處理 Unicode 字串
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
- Unicode, marshaling strings
ms.assetid: 96c2141d-6c5d-43ef-a1aa-5785afb9a9aa
ms.openlocfilehash: da320dbd41e7158e3bc2482b96a73c1f4728a01b
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414304"
---
# <a name="how-to-marshal-unicode-strings-using-c-interop"></a>如何：使用 C++ Interop 封送處理 Unicode 字串

本主題將示範 Visual C++ 互通性的一個 facet。 如需詳細資訊，請參閱 [使用 c + + Interop (隱含的 PInvoke) ](../dotnet/using-cpp-interop-implicit-pinvoke.md)。

下列程式碼範例使用 [managed、非](../preprocessor/managed-unmanaged.md) 受控 #pragma 指示詞，在相同的檔案中執行 managed 和非受控函式，但這些函式在個別檔案中定義時，會以相同的方式相交互操作。 只包含非受控函式的檔案不需要使用 [/clr (Common Language Runtime 編譯) ](../build/reference/clr-common-language-runtime-compilation.md)來進行編譯。

本主題將示範如何將 Unicode 字串從 managed 傳遞至非受控函式，反之亦然。 如需與其他字串類型交互操作，請參閱下列主題：

- [如何：使用 c + + Interop 封送處理 ANSI 字串](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)

- [如何：使用 c + + Interop 封送處理 COM 字串](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)

## <a name="example-pass-unicode-string-from-managed-to-unmanaged-function"></a>範例：將 Unicode 字串從 managed 傳遞至非受控函式

若要將 Unicode 字串從 managed 傳遞至非受控函式，在) Vcclr 中宣告的 PtrToStringChars 函式 (可以用來存取儲存 managed 字串的記憶體。 因為此位址會傳遞至原生函式，所以將記憶體釘選 [pin_ptr (c + +/cli) ](../extensions/pin-ptr-cpp-cli.md) 以避免在執行非受控函式時，發生垃圾收集迴圈的情況下，將字串資料重新放置，是很重要的。

```cpp
// MarshalUnicode1.cpp
// compile with: /clr
#include <iostream>
#include <stdio.h>
#include <vcclr.h>

using namespace std;

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

void NativeTakesAString(const wchar_t* p) {
   printf_s("(native) received '%S'\n", p);
}

#pragma managed

int main() {
   String^ s = gcnew String("test string");
   pin_ptr<const wchar_t> str = PtrToStringChars(s);

   Console::WriteLine("(managed) passing string to native func...");
   NativeTakesAString( str );
}
```

## <a name="example-data-marshaling-required-to-access-unicode-string"></a>範例：存取 Unicode 字串所需的資料封送處理

下列範例示範在非受控函式所呼叫的 managed 函式中存取 Unicode 字串所需的資料封送處理。 Managed 函式在接收原生 Unicode 字串時，會使用方法將它轉換成 managed 字串 <xref:System.Runtime.InteropServices.Marshal.PtrToStringUni%2A> 。

```cpp
// MarshalUnicode2.cpp
// compile with: /clr
#include <iostream>

using namespace std;
using namespace System;
using namespace System::Runtime::InteropServices;

#pragma managed

void ManagedStringFunc(wchar_t* s) {
   String^ ms = Marshal::PtrToStringUni((IntPtr)s);
   Console::WriteLine("(managed) received '{0}'", ms);
}

#pragma unmanaged

void NativeProvidesAString() {
   cout << "(unmanaged) calling managed func...\n";
   ManagedStringFunc(L"test string");
}

#pragma managed

int main() {
   NativeProvidesAString();
}
```

## <a name="see-also"></a>另請參閱

[使用 c + + Interop (隱含 PInvoke) ](../dotnet/using-cpp-interop-implicit-pinvoke.md)
