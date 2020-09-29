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
ms.openlocfilehash: 5d0427962ddb7d6409f07b99c0f618b340ee00df
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414291"
---
# <a name="how-to-marshal-callbacks-and-delegates-by-using-c-interop"></a>如何：使用 C++ Interop 封送處理回呼和委派

本主題將示範如何使用 Visual C++，將回呼和委派的封送處理 (受控和非受控碼之間的 managed 版本) 。

下列程式碼範例使用 [managed、非](../preprocessor/managed-unmanaged.md) 受控 #pragma 指示詞，在相同的檔案中執行 managed 和非受控函式，但是也可以在個別的檔案中定義函數。 只包含非受控函式的檔案不需要使用 [/clr (Common Language Runtime 編譯) ](../build/reference/clr-common-language-runtime-compilation.md)來進行編譯。

## <a name="example-configure-unmanaged-api-to-trigger-managed-delegate"></a>範例：設定非受控 API 來觸發受管理的委派

下列範例示範如何設定非受控 API 來觸發受管理的委派。 建立 managed 委派，並使用其中一個 interop 方法 <xref:System.Runtime.InteropServices.Marshal.GetFunctionPointerForDelegate%2A> 來取得委派的基礎進入點。 此位址接著會傳遞至非受控函式，而不需要知道它是實作為 managed 函式的事實。

請注意，有可能（但不是必要）使用 [pin_ptr (c + +/cli) ](../extensions/pin-ptr-cpp-cli.md) 來釘選委派，以防止垃圾收集行程重新找出或處置委派。 需要預防過多的垃圾收集，但釘選可提供比所需更多的保護，因為它會防止收集但也會防止重新配置。

如果委派是由垃圾收集重新置放，則不會影響 underlaying managed 回呼，因此 <xref:System.Runtime.InteropServices.GCHandle.Alloc%2A> 會用來加入委派的參考，以允許重新配置委派，但防止處置。 使用 GCHandle 而非 pin_ptr 可減少 managed 堆積的分散潛力。

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

## <a name="example-function-pointer-stored-by-unmanaged-api"></a>範例：非受控 API 儲存的函式指標

下列範例與上一個範例類似，但在此情況下，未受管理的 API 會儲存提供的函式指標，因此可以隨時叫用，要求將垃圾收集視為任意時間長度。 因此，下列範例會使用的全域實例 <xref:System.Runtime.InteropServices.GCHandle> ，以防止委派重新放置，與函數範圍無關。 如第一個範例中所述，這些範例不需要使用 pin_ptr，但在此情況下，不會有任何作用，因為 pin_ptr 的範圍僅限於單一函式。

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

## <a name="see-also"></a>另請參閱

[使用 c + + Interop (隱含 PInvoke) ](../dotnet/using-cpp-interop-implicit-pinvoke.md)
