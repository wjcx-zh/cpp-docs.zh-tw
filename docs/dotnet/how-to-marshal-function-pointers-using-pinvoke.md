---
title: HOW TO：封送處理函式指標使用 PInvoke
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- data marshaling [C++], callbacks and delegates
- interop [C++], callbacks and delegates
- platform invoke [C++], callbacks and delegates
- marshaling [C++], callbacks and delegates
ms.assetid: dcf396fd-a91d-49c0-ab0b-1ea160668a89
ms.openlocfilehash: 031bda0f93d6a95aa3c774553aefca0647d0518c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400561"
---
# <a name="how-to-marshal-function-pointers-using-pinvoke"></a>HOW TO：封送處理函式指標使用 PInvoke

本主題說明如何在受管理的委派時與相互操作 unmanaged 函式使用.NET Framework P/Invoke 功能可用來取代函式指標。 不過，VisualC++程式設計人員是鼓勵使用C++Interop 功能，而是 （如果可能） 因為 P/Invoke 提供報告，不是類型安全，並可能會非常繁瑣實作小小的編譯時期錯誤。 如果未受管理的 API 會封裝成 DLL，而且沒有可用的原始程式碼，P/Invoke 就會是唯一的選項。 否則，請參閱下列主題：

- [使用 C++ Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)

- [如何：使用 C++ Interop 封送處理回呼和委派](../dotnet/how-to-marshal-callbacks-and-delegates-by-using-cpp-interop.md)

Unmanaged 的 Api，稱為 引數可以是從 managed 程式碼取代原生函式指標的受管理的委派，採用函式指標。 編譯器會自動封送處理至 unmanaged 函式的委派函式指標，並將必要的 managed/unmanaged 轉換程式碼插入。

## <a name="example"></a>範例

下列程式碼是由 unmanaged 和 managed 的模組所組成。 未受管理的模組會定義稱為 TakesCallback 接受函式指標的函式的 DLL。 此位址用來執行函式。

受管理的模組定義委派，其中會封送處理函式指標的原生程式碼，並使用<xref:System.Runtime.InteropServices.DllImportAttribute>公開給 managed 程式碼的原生 TakesCallback 函式的屬性。 在主要函數中，是建立委派的執行個體，並將其傳遞給 TakesCallback 函式中。 程式輸出示範執行此函式時，取得原生 TakesCallback 函式。

Managed 函式會隱藏的受管理的委派，以避免.NET Framework 記憶體回收原生函式執行時，重新放置委派記憶體回收。

```cpp
// TraditionalDll5.cpp
// compile with: /LD /EHsc
#include <iostream>
#define TRADITIONALDLL_EXPORTS
#ifdef TRADITIONALDLL_EXPORTS
#define TRADITIONALDLL_API __declspec(dllexport)
#else
#define TRADITIONALDLL_API __declspec(dllimport)
#endif

extern "C" {
   /* Declare an unmanaged function type that takes two int arguments
      Note the use of __stdcall for compatibility with managed code */
   typedef int (__stdcall *CALLBACK)(int);
   TRADITIONALDLL_API int TakesCallback(CALLBACK fp, int);
}

int TakesCallback(CALLBACK fp, int n) {
   printf_s("[unmanaged] got callback address, calling it...\n");
   return fp(n);
}
```

```cpp
// MarshalDelegate.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

public delegate int GetTheAnswerDelegate(int);
public value struct TraditionalDLL {
   [DllImport("TraditionalDLL5.dll")]
   static public int TakesCallback(GetTheAnswerDelegate^ pfn, int n);
};

int GetNumber(int n) {
   Console::WriteLine("[managed] callback!");
   static int x = 0;
   ++x;
   return x + n;
}

int main() {
   GetTheAnswerDelegate^ fp = gcnew GetTheAnswerDelegate(GetNumber);
   pin_ptr<GetTheAnswerDelegate^> pp = &fp;
   Console::WriteLine("[managed] sending delegate as callback...");

   int answer = TraditionalDLL::TakesCallback(fp, 42);
}
```

請注意沒有部分的 dll 會使用傳統的 managed 程式碼以 #include 指示詞。 事實上，DLL 會在執行階段存取，因此問題函式匯入與<xref:System.Runtime.InteropServices.DllImportAttribute>將不會在編譯時期偵測。

## <a name="see-also"></a>另請參閱

[在 C++ 中使用明確的 PInvoke (DllImport 屬性)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
