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
ms.openlocfilehash: 3113f0bd04fc8433dc4c7f443914fca9245a54f4
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414330"
---
# <a name="how-to-marshal-com-strings-using-c-interop"></a>如何：使用 C++ Interop 封送處理 COM 字串

本主題示範 BSTR 如何 (COM 程式設計中偏好的基底字元串格式) 可以從 managed 傳遞至非受控函式，反之亦然。 如需與其他字串類型交互操作，請參閱下列主題：

- [如何：使用 c + + Interop 封送處理 Unicode 字串](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)

- [如何：使用 c + + Interop 封送處理 ANSI 字串](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)

下列程式碼範例使用 [managed、非](../preprocessor/managed-unmanaged.md) 受控 #pragma 指示詞，在相同的檔案中執行 managed 和非受控函式，但這些函式在個別檔案中定義時，會以相同的方式相交互操作。 只包含非受控函式的檔案不需要使用 [/clr (Common Language Runtime 編譯) ](../build/reference/clr-common-language-runtime-compilation.md)來進行編譯。

## <a name="example-pass-bstr-from-managed-to-unmanaged-function"></a>範例：將 BSTR 從 managed 傳遞至非受控函式

下列範例示範 BSTR 如何 (COM 程式設計中使用的字串格式) 可從 managed 傳遞至非受控函式。 呼叫 managed 函式會使用 <xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A> 來取得 .Net system.string 內容之 BSTR 表示的位址。 這個指標是使用 [pin_ptr (c + +/cli) ](../extensions/pin-ptr-cpp-cli.md) 來確保其實體位址在非受控函式執行期間，不會在垃圾收集週期中變更。 在 [pin_ptr (c + +/cli) ](../extensions/pin-ptr-cpp-cli.md) 超出範圍之前，禁止垃圾收集行程移動記憶體。

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

## <a name="example-pass-bstr-from-unmanaged-to-managed-function"></a>範例：將 BSTR 從非受控函式傳遞給 managed 函式

下列範例會示範如何將 BSTR 從非受控函式傳遞至 managed 函式。 接收 managed 函式可以使用中的字串做為 BSTR，或是用 <xref:System.Runtime.InteropServices.Marshal.PtrToStringBSTR%2A> 來將它轉換成， <xref:System.String> 以便與其他 managed 函數搭配使用。 因為代表 BSTR 的記憶體是在非受控堆積上配置的，所以不需要釘選，因為非受控堆積上沒有垃圾收集。

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

## <a name="see-also"></a>另請參閱

[使用 c + + Interop (隱含 PInvoke) ](../dotnet/using-cpp-interop-implicit-pinvoke.md)
