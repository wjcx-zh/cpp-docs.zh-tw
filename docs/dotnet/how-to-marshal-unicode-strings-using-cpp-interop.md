---
title: 如何： 使用 c + + Interop 封送處理 Unicode 字串 |Microsoft Docs
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
- Unicode, marshaling strings
ms.assetid: 96c2141d-6c5d-43ef-a1aa-5785afb9a9aa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 42aba2595792cca6ced3febea9890dabfb87aa14
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46382241"
---
# <a name="how-to-marshal-unicode-strings-using-c-interop"></a>如何：使用 C++ Interop 封送處理 Unicode 字串

本主題會示範一個 facet 的 Visual c + + 的互通性。 如需詳細資訊，請參閱 <<c0> [ 使用 c + + Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)。

下列程式碼範例使用[managed、 unmanaged](../preprocessor/managed-unmanaged.md) #pragma 指示詞來實作 managed 和 unmanaged 函式在相同的檔案，但如果在不同的檔案中定義這些函式交互操作方式相同。 包含 unmanaged 的函式的檔案不需要進行編譯[/clr （Common Language Runtime 編譯）](../build/reference/clr-common-language-runtime-compilation.md)。

本主題示範了如何 Unicode 字串可以傳遞從 managed 至 unmanaged 函式，反之亦然。 與其他字串類型的交互操作，請參閱下列主題：

- [如何：使用 C++ Interop 封送處理 ANSI 字串](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)

- [如何：使用 C++ Interop 封送處理 COM 字串](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)

## <a name="example"></a>範例

若要從受管理的 unmanaged 函式傳遞 Unicode 字串，您可以使用 PtrToStringChars 函式 （Vcclr.h 中宣告） 中儲存的 managed 的字串的記憶體存取。 因為這個位址會傳遞至原生函式中，務必具有釘選記憶體[pin_ptr (C + + /cli CLI)](../windows/pin-ptr-cpp-cli.md)以防止遭到重新配置的字串資料，應該記憶體回收週期發生時unmanaged 函式會執行。

```
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

## <a name="example"></a>範例

下列範例示範資料封送處理，才能存取 unmanaged 的函式呼叫 managed 函式的 Unicode 字串。 受管理的函式，在接收原生的 Unicode 字串，將它轉換成 managed 的字串，使用<xref:System.Runtime.InteropServices.Marshal.PtrToStringUni%2A>方法。

```
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

[使用 C++ Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)