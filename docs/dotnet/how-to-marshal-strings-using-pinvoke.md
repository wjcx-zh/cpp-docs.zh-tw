---
title: 如何：使用 PInvoke 封送處理字串
ms.custom: get-started-article
ms.date: 09/09/2016
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- data marshaling [C++], strings
- platform invoke [C++], strings
ms.assetid: bcc75733-7337-4d9b-b1e9-b95a98256088
ms.openlocfilehash: e89177261aa32d34ea392030078d4088ea61e2a5
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988442"
---
# <a name="how-to-marshal-strings-using-pinvoke"></a>如何：使用 PInvoke 封送處理字串

本主題說明如何使用 CLR 字串類型 System：： String 來呼叫接受 C 樣式字串的原生函式，以 .NET Framework 平台叫用支援。 建議C++ Visual 程式設計人員改用C++ Interop 功能（可能的話），因為 P/Invoke 提供的編譯階段錯誤報表很少，而且不是型別安全，而且可能很繁瑣。 如果非受控 API 封裝為 DLL，而原始程式碼無法使用，則 P/Invoke 是唯一的選項，否則請參閱[使用C++ Interop （隱含 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)。

受控和非受控字串在記憶體中的配置方式不同，因此將字串從 managed 傳遞至非受控函式需要 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性來指示編譯器插入必要的轉換機制，以便正確且安全地封送處理字串資料。

就像只使用內建資料類型的函式一樣，<xref:System.Runtime.InteropServices.DllImportAttribute> 是用來將 managed 進入點宣告為原生函式，但--用於傳遞字串，而不是將這些進入點定義為採用 C 樣式字串，而是可以改用 <xref:System.String> 類型的控制碼。 這會提示編譯器插入執行必要轉換的程式碼。 對於接受字串之非受控函式中的每個函式引數，應該使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性來指示字串物件應該以 C 樣式字串的形式封送處理至原生函式。

封送處理器會將非受控函式的呼叫包裝在隱藏的包裝函式常式中，將 managed 字串釘選並複製到非受控內容中的本機配置字串，然後再傳遞給非受控函式。 當非受控函式傳回時，包裝函式會刪除資源，如果它是在堆疊上，則會在包裝函式超出範圍時回收。 非受控函式不負責此記憶體。 未受管理的程式碼只會建立和刪除由它自己的 CRT 所設定之堆積中的記憶體，因此使用不同 CRT 版本的封送處理器並不會有任何問題。

如果您的非受控函式傳回字串（做為傳回值或 out 參數），封送處理器會將它複製到新的 managed 字串，然後釋放記憶體。 如需詳細資訊，請參閱[預設封送處理行為](/dotnet/framework/interop/default-marshaling-behavior)和[使用平台叫用封送處理資料](/dotnet/framework/interop/marshaling-data-with-platform-invoke)。

## <a name="example"></a>範例

下列程式碼是由不受管理的和受控模組所組成。 非受控模組是定義名為 TakesAString 之函式的 DLL，其接受以 char * 格式表示的 C 樣式 ANSI 字串。 受控模組是一種命令列應用程式，它會匯入 TakesAString 函式，但會將它定義為接受 managed System.string，而不是 char\*。 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性是用來指示呼叫 TakesAString 時，managed 字串應該如何封送處理。

```cpp
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

```cpp
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

這項技術會導致在非受控堆積上建立字串的複本，因此原生函式對字串所做的變更將不會反映在字串的 managed 複本中。

請注意，不會透過傳統的 #include 指示詞，將 DLL 的任何部分公開給 managed 程式碼。 事實上，DLL 只能在執行時間存取，因此使用 `DllImport` 匯入的函式會在編譯時期偵測到問題。

## <a name="see-also"></a>請參閱

[在 C++ 中使用明確的 PInvoke (DllImport 屬性)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
