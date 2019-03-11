---
title: HOW TO：封送處理回呼和委派使用 c + + Interop
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
ms.openlocfilehash: d3814ffbcd23168a9727b1b1d73e2c825639a9c5
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57739226"
---
# <a name="how-to-marshal-callbacks-and-delegates-by-using-c-interop"></a>HOW TO：封送處理回呼和委派使用 c + + Interop

本主題示範回呼的封送處理，並使用 Visual c + + 中的 managed 和 unmanaged 程式碼之間會委派 （回呼的受管理的版本）。

下列程式碼範例使用[managed、 unmanaged](../preprocessor/managed-unmanaged.md) #pragma 指示詞來實作 managed 和 unmanaged 函式在相同的檔案，但函式也可定義在個別的檔案。 包含 unmanaged 的函式的檔案不需要進行編譯[/clr （Common Language Runtime 編譯）](../build/reference/clr-common-language-runtime-compilation.md)。

## <a name="example"></a>範例

下列範例示範如何設定 unmanaged 的 API，以觸發程序的受管理的委派。 建立受管理的委派和 interop 方法的其中一個<xref:System.Runtime.InteropServices.Marshal.GetFunctionPointerForDelegate%2A>，用來擷取基礎的進入點的委派。 此位址再傳遞至 unmanaged 函式，不需要知道的事實，它會實作為 managed 函式會呼叫它。

請注意，是可行的但並非必要，釘選使用的委派[pin_ptr (C + + /cli CLI)](../windows/pin-ptr-cpp-cli.md)可防止它們被重新位於或由記憶體回收行程處置。 需要防止不當記憶體回收，但是 pin 會提供比所需的因為它可防止集合也會防止重新配置更多的保護。

如果進行記憶體回收重新位於委派，則它不會影響受管理的 underlaying 回呼中，因此<xref:System.Runtime.InteropServices.GCHandle.Alloc%2A>用來將參考加入委派，讓重新配置的委派，但防止處置。 使用 GCHandle，而不 pin_ptr，可降低 managed 堆積的片段可能性。

```
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

下列範例類似上述範例中，但在此情況下提供的函式指標會儲存未受管理的 api，讓它可以叫用在任何時候需要記憶體回收會隱藏任意長度的時間。 如此一來，下列範例會使用全域執行個體<xref:System.Runtime.InteropServices.GCHandle>以防止委派重新定位，獨立於函式範圍。 第一個範例中所述，使用 pin_ptr 不需要為這些範例中，但在此情況下不會運作，因為 pin_ptr 的範圍僅限於單一函式。

```
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

[使用 C++ Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
