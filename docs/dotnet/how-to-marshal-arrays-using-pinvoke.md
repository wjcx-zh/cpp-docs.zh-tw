---
title: 如何： 使用 PInvoke 封送處理陣列 |Microsoft Docs
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- marshaling [C++], arrays
- platform invoke [C++], arrays
- interop [C++], arrays
- data marshaling [C++], arrays
ms.assetid: a1237797-a2da-4df4-984a-6333ed3af406
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9c07aba54f621011d2dd4831d7dfb6b536073fa9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46395683"
---
# <a name="how-to-marshal-arrays-using-pinvoke"></a>如何：使用 PInvoke 封送處理陣列

本主題說明如何在原生函式會接受 C 樣式字串可使用 CLR 字串型別呼叫<xref:System.String>使用.NET Framework 平台叫用的支援。 Visual c + + 程式設計人員會建議改為使用 c + + Interop 功能 （如果可能），因為 P/Invoke 提供極少的編譯時期錯誤，報告，不是類型安全，而且可能會非常繁瑣的實作。 如果未受管理的 API 會封裝成 DLL，而且沒有可用的原始程式碼，P/Invoke 是唯一的選項 (否則請參閱[使用 c + + Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md))。

## <a name="example"></a>範例

原生和 managed 陣列是以不同的方式在記憶體中配置，因為跨 managed/unmanaged 界限成功傳遞需要轉換，或封送處理。 本主題示範如何簡單 (blitable) 項目的陣列可以傳遞至原生函式從 managed 程式碼。

如為 true 的 managed/unmanaged 資料封送處理一般情況下，<xref:System.Runtime.InteropServices.DllImportAttribute>屬性用來建立將用於每個原生函式的 managed 的進入點。 在採用陣列當做引數，函式的情況下<xref:System.Runtime.InteropServices.MarshalAsAttribute>屬性必須也用來指定編譯器如何將資料會被封送處理。 在下列範例中，<xref:System.Runtime.InteropServices.UnmanagedType>列舉型別用來表示，managed 的陣列會封送處理為 C 樣式陣列。

下列程式碼是由 unmanaged 和 managed 的模組所組成。 未受管理的模組會定義接受整數陣列的函式的 DLL。 第二個模組是受管理的命令列應用程式匯入此函式，但定義方面的受管理的陣列，並使用<xref:System.Runtime.InteropServices.MarshalAsAttribute>屬性來指定陣列，應該轉換成原生陣列時呼叫。

受管理的模組是使用 /clr 所編譯。

```cpp
// TraditionalDll4.cpp
// compile with: /LD /EHsc
#include <iostream>

#define TRADITIONALDLL_EXPORTS
#ifdef TRADITIONALDLL_EXPORTS
#define TRADITIONALDLL_API __declspec(dllexport)
#else
#define TRADITIONALDLL_API __declspec(dllimport)
#endif

extern "C" {
   TRADITIONALDLL_API void TakesAnArray(int len, int[]);
}

void TakesAnArray(int len, int a[]) {
   printf_s("[unmanaged]\n");
   for (int i=0; i<len; i++)
      printf("%d = %d\n", i, a[i]);
}
```

```cpp
// MarshalBlitArray.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

value struct TraditionalDLL {
   [DllImport("TraditionalDLL4.dll")]
   static public void TakesAnArray(
   int len,[MarshalAs(UnmanagedType::LPArray)]array<int>^);
};

int main() {
   array<int>^ b = gcnew array<int>(3);
   b[0] = 11;
   b[1] = 33;
   b[2] = 55;
   TraditionalDLL::TakesAnArray(3, b);

   Console::WriteLine("[managed]");
   for (int i=0; i<3; i++)
      Console::WriteLine("{0} = {1}", i, b[i]);
}
```

請注意沒有部分的 dll 會公開給 managed 程式碼，透過傳統 #include 指示詞。 事實上，DLL 會在執行階段只存取，因此問題函式匯入與<xref:System.Runtime.InteropServices.DllImportAttribute>將不會在編譯時期偵測。

## <a name="see-also"></a>另請參閱

[在 C++ 中使用明確的 PInvoke (DllImport 屬性)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)