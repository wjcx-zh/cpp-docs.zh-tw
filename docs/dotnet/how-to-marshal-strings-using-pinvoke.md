---
title: 如何：使用 PInvoke 封送處理字串
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- data marshaling [C++], strings
- platform invoke [C++], strings
ms.assetid: bcc75733-7337-4d9b-b1e9-b95a98256088
ms.openlocfilehash: 86ce065da5c214c0da803ad53d19eaec3de5efb4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50598116"
---
# <a name="how-to-marshal-strings-using-pinvoke"></a>如何：使用 PInvoke 封送處理字串

本主題說明如何在原生函式會接受 C 樣式字串可使用的 CLR 字串呼叫輸入使用.NET Framework 平台叫用支援的 system:: string。 Visual c + + 程式設計人員會建議改為使用 c + + Interop 功能 （如果可能），因為 P/Invoke 提供極少的編譯時期錯誤，報告，不是類型安全，而且可能會非常繁瑣的實作。 如果未受管理的 API 會封裝為 DLL，而且沒有可用的原始程式碼，P/Invoke 是唯一的選項，但否則看到[使用 c + + Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)。

Managed 和 unmanaged 字串會以不同的方式在記憶體中配置，因此傳遞字串從 managed 到 unmanaged 函式需要<xref:System.Runtime.InteropServices.MarshalAsAttribute>屬性指示編譯器插入封送處理字串資料的必要的轉換機制正確且安全地。

如同使用只有內建資料型別，函式<xref:System.Runtime.InteropServices.DllImportAttribute>用來宣告 managed 的進入點，執行原生函式中，-但傳遞字串，而不是定義為 C 樣式字串的控制代碼的這些進入點<xref:System.String>類型可以改為使用。 這會提示編譯器插入程式碼來執行必要的轉換。 每個函式引數在 unmanaged 函式可接受 string，<xref:System.Runtime.InteropServices.MarshalAsAttribute>屬性應該用來表示字串物件，應該封送處理為 C 樣式字串原生函式。

## <a name="example"></a>範例

下列程式碼是由未受管理 」 和 「 受管理的模組所組成。 未受管理的模組是定義呼叫 TakesAString 接受 char * 形式 ANSI C 樣式字串到函式的 DLL。 受管理的模組是命令列應用程式匯入 TakesAString 函式，但定義為受管理的 System.String，而不是 char\*。 <xref:System.Runtime.InteropServices.MarshalAsAttribute>屬性用來指示如何的 managed 的字串應該封送處理呼叫 TakesAString 時。

```
// TraditionalDll2.cpp
// compile with: /LD /EHsc
#include <windows.h>
#include <stdio.h>
#include <iostream>

using namespace std;

#define TRADITIONALDLL_EXPORTS
#ifdef TRADITIONALDLL_EXPORTS
#define TRADITIONALDLL_API __declspec(dllexport)
#else
#define TRADITIONALDLL_API __declspec(dllimport)
#endif

extern "C" {
   TRADITIONALDLL_API void TakesAString(char*);
}

void TakesAString(char* p) {
   printf_s("[unmanaged] %s\n", p);
}
```

```
// MarshalString.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

value struct TraditionalDLL
{
   [DllImport("TraditionalDLL2.dll")]
      static public void
      TakesAString([MarshalAs(UnmanagedType::LPStr)]String^);
};

int main() {
   String^ s = gcnew String("sample string");
    Console::WriteLine("[managed] passing managed string to unmanaged function...");
   TraditionalDLL::TakesAString(s);
   Console::WriteLine("[managed] {0}", s);
}
```

這項技術會造成 unmanaged 堆積中，字串對原生函式所做的變更將不會反映在 managed 字串的複本，因此建構字串的複本。

請注意沒有部分的 dll 會公開給 managed 程式碼，透過傳統 #include 指示詞。 事實上，DLL 會在執行階段存取，因此問題函式匯入與`DllImport`將不會在編譯時期偵測。

## <a name="see-also"></a>另請參閱

[在 C++ 中使用明確的 PInvoke (DllImport 屬性)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)