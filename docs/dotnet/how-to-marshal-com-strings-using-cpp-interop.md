---
title: 如何：使用 C++ Interop 封送處理 COM 字串
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
- COM [C++], marshaling strings
ms.assetid: 06590759-bf99-4e34-a3a9-4527ea592cc2
ms.openlocfilehash: 8dfdad892261d5ae2d3494734458e1447f8ebd7c
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988461"
---
# <a name="how-to-marshal-com-strings-using-c-interop"></a>如何：使用 C++ Interop 封送處理 COM 字串

本主題示範如何將 BSTR （COM 程式設計中的基底字元串格式）從 managed 傳遞至非受控函式，反之亦然。 如需與其他字串類型互通，請參閱下列主題：

- [如何：使用 C++ Interop 封送處理 Unicode 字串](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)

- [如何：使用 C++ Interop 封送處理 ANSI 字串](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)

下列程式碼範例會使用[managed、非](../preprocessor/managed-unmanaged.md)受控 #pragma 指示詞，在同一個檔案中執行 managed 和非受控函式，但如果在個別的檔案中定義，則這些函式會以相同的方式進行交互作用。 僅包含非受控函式的檔案不需要使用[/clr （Common Language Runtime 編譯）](../build/reference/clr-common-language-runtime-compilation.md)進行編譯。

## <a name="example"></a>範例

下列範例示範如何將 BSTR （在 COM 程式設計中使用的字串格式）傳遞至非受控函式。 呼叫的 managed 函式會使用 <xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A> 來取得 .NET System.string 內容之 BSTR 表示的位址。 這個指標會使用[pin_ptr （C++/cli）](../extensions/pin-ptr-cpp-cli.md)釘選，以確保在執行非受控函式時，不會在垃圾收集週期變更其實體位址。 在[pin_ptr （C++/cli）](../extensions/pin-ptr-cpp-cli.md)超出範圍之前，垃圾收集行程禁止移動記憶體。

```cpp
// MarshalBSTR1.cpp
// compile with: /clr
#define WINVER 0x0502
#define _AFXDLL
#include <afxwin.h>

#include <iostream>
using namespace std;

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

void NativeTakesAString(BSTR bstr) {
   printf_s("%S", bstr);
}

#pragma managed

int main() {
   String^ s = "test string";

   IntPtr ip = Marshal::StringToBSTR(s);
   BSTR bs = static_cast<BSTR>(ip.ToPointer());
   pin_ptr<BSTR> b = &bs;

   NativeTakesAString( bs );
   Marshal::FreeBSTR(ip);
}
```

## <a name="example"></a>範例

下列範例會示範如何從非受控函式將 BSTR 傳遞至非受控函式。 接收的 managed 函數可以使用中的字串做為 BSTR，或使用 <xref:System.Runtime.InteropServices.Marshal.PtrToStringBSTR%2A> 將它轉換成 <xref:System.String> 以與其他 managed 函式搭配使用。 因為代表 BSTR 的記憶體是在非受控堆積上配置，所以不需要固定，因為非受控堆積上不會進行垃圾收集。

```cpp
// MarshalBSTR2.cpp
// compile with: /clr
#define WINVER 0x0502
#define _AFXDLL
#include <afxwin.h>

#include <iostream>
using namespace std;

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma managed

void ManagedTakesAString(BSTR bstr) {
   String^ s = Marshal::PtrToStringBSTR(static_cast<IntPtr>(bstr));
   Console::WriteLine("(managed) convered BSTR to String: '{0}'", s);
}

#pragma unmanaged

void UnManagedFunc() {
   BSTR bs = SysAllocString(L"test string");
   printf_s("(unmanaged) passing BSTR to managed func...\n");
   ManagedTakesAString(bs);
}

#pragma managed

int main() {
   UnManagedFunc();
}
```

## <a name="see-also"></a>請參閱

[使用 C++ Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
