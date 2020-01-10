---
title: 如何：使用 C++ Interop 封送處理回呼和委派
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- data marshaling [C++], callbacks and delegates
- C++ Interop, callbacks and delegates
- interop [C++], callbacks and delegates
- delegates [C++], marshaling
- marshaling [C++], callbacks and delegates
- callbacks [C++], marshaling
ms.assetid: 2313e9eb-5df9-4367-be0f-14b4712d8d2d
ms.openlocfilehash: 592eae0ff59baddb79b810d46669b78ecc801155
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988186"
---
# <a name="how-to-marshal-callbacks-and-delegates-by-using-c-interop"></a>如何：使用 C++ Interop 封送處理回呼和委派

本主題示範如何使用視覺效果C++，在 managed 和非受控碼之間進行回呼和委派的封送處理（managed 版本的回呼）。

下列程式碼範例會使用[managed、非](../preprocessor/managed-unmanaged.md)受控 #pragma 指示詞，在同一個檔案中執行 managed 和非受控函式，但也可以在不同的檔案中定義函式。 僅包含非受控函式的檔案不需要使用[/clr （Common Language Runtime 編譯）](../build/reference/clr-common-language-runtime-compilation.md)進行編譯。

## <a name="example"></a>範例

下列範例示範如何設定非受控 API 以觸發 managed 委派。 建立 managed 委派，並使用其中一個 interop 方法（<xref:System.Runtime.InteropServices.Marshal.GetFunctionPointerForDelegate%2A>）來抓取委派的基礎進入點。 此位址接著會傳遞至非受控函式，它會呼叫它，而不知道它會實作為 managed 函式。

請注意，您可以使用[pin_ptr （C++/cli）](../extensions/pin-ptr-cpp-cli.md)來釘選委派，以防止垃圾收集行程重新找出或處置它，這是可行的，但不是必要的。 需要進行過早垃圾收集的保護，但釘選提供的保護比所需的還多，因為它會防止收集，同時也會防止重新配置。

如果委派是由垃圾收集重新置放，則不會影響 underlaying managed 回呼，因此 <xref:System.Runtime.InteropServices.GCHandle.Alloc%2A> 是用來新增委派的參考，允許重新配置委派，但防止處置。 使用 GCHandle 而不是 pin_ptr 可減少受控堆積的分散可能性。

```cpp
// MarshalDelegate1.cpp
// compile with: /clr
#include <iostream>

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

// Declare an unmanaged function type that takes two int arguments
// Note the use of __stdcall for compatibility with managed code
typedef int (__stdcall *ANSWERCB)(int, int);

int TakesCallback(ANSWERCB fp, int n, int m) {
   printf_s("[unmanaged] got callback address, calling it...\n");
   return fp(n, m);
}

#pragma managed

public delegate int GetTheAnswerDelegate(int, int);

int GetNumber(int n, int m) {
   Console::WriteLine("[managed] callback!");
   return n + m;
}

int main() {
   GetTheAnswerDelegate^ fp = gcnew GetTheAnswerDelegate(GetNumber);
   GCHandle gch = GCHandle::Alloc(fp);
   IntPtr ip = Marshal::GetFunctionPointerForDelegate(fp);
   ANSWERCB cb = static_cast<ANSWERCB>(ip.ToPointer());
   Console::WriteLine("[managed] sending delegate as callback...");

// force garbage collection cycle to prove
// that the delegate doesn't get disposed
   GC::Collect();

   int answer = TakesCallback(cb, 243, 257);

// release reference to delegate
   gch.Free();
}
```

## <a name="example"></a>範例

下列範例與前一個範例類似，但在此情況下，所提供的函式指標是由非受控 API 儲存，因此可以在任何時間叫用，以要求抑制垃圾收集一段任意時間長度。 因此，下列範例會使用 <xref:System.Runtime.InteropServices.GCHandle> 的全域實例，以避免將委派重新置放，與函式範圍無關。 如第一個範例所討論，使用 pin_ptr 在這些範例中是不必要的，但在此情況下，您仍然無法運作，因為 pin_ptr 的範圍僅限於單一函式。

```cpp
// MarshalDelegate2.cpp
// compile with: /clr
#include <iostream>

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

// Declare an unmanaged function type that takes two int arguments
// Note the use of __stdcall for compatibility with managed code
typedef int (__stdcall *ANSWERCB)(int, int);
static ANSWERCB cb;

int TakesCallback(ANSWERCB fp, int n, int m) {
   cb = fp;
   if (cb) {
      printf_s("[unmanaged] got callback address (%d), calling it...\n", cb);
      return cb(n, m);
   }
   printf_s("[unmanaged] unregistering callback");
   return 0;
}

#pragma managed

public delegate int GetTheAnswerDelegate(int, int);

int GetNumber(int n, int m) {
   Console::WriteLine("[managed] callback!");
   static int x = 0;
   ++x;

   return n + m + x;
}

static GCHandle gch;

int main() {
   GetTheAnswerDelegate^ fp = gcnew GetTheAnswerDelegate(GetNumber);

   gch = GCHandle::Alloc(fp);

   IntPtr ip = Marshal::GetFunctionPointerForDelegate(fp);
   ANSWERCB cb = static_cast<ANSWERCB>(ip.ToPointer());
   Console::WriteLine("[managed] sending delegate as callback...");

   int answer = TakesCallback(cb, 243, 257);

   // possibly much later (in another function)...

   Console::WriteLine("[managed] releasing callback mechanisms...");
   TakesCallback(0, 243, 257);
   gch.Free();
}
```

## <a name="see-also"></a>請參閱

[使用 C++ Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
