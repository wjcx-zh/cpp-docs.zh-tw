---
title: HOW TO：使用 PInvoke 從 Managed 程式碼呼叫原生 Dll
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- platform invoke [C++], calling native DLLs
- interop [C++], calling native DLLs
- marshaling [C++], calling native DLLs
- data marshaling [C++], calling native DLLs
ms.assetid: 3273eb4b-38d1-4619-92a6-71bda542be72
ms.openlocfilehash: b36496690c4d83837a6dff1752f3f0db514869eb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "70311705"
---
# <a name="how-to-call-native-dlls-from-managed-code-using-pinvoke"></a>作法：使用 PInvoke 從 Managed 程式碼呼叫原生 Dll

您可以使用平台叫用（P/Invoke）功能，從 managed 程式碼呼叫未受管理的 Dll 中所實作用的函式。 如果 DLL 的原始程式碼無法使用，P/Invoke 是唯一可進行交互操作的選項。 不過，不同于其他 .NET 語言， C++ Visual 提供 P/Invoke 的替代方案。 如需詳細資訊，請參閱[使用C++ Interop （隱含 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)。

## <a name="example"></a>範例

下列程式碼範例會使用 Win32 [GetSystemMetrics](/windows/win32/api/winuser/nf-winuser-getsystemmetrics)函式來抓取螢幕的目前解析度（以圖元為單位）。

針對只使用內建類型做為引數和傳回值的函式，不需要額外的工作。 其他資料類型（例如函式指標、陣列和結構）則需要額外的屬性，以確保正確的資料封送處理。

雖然並非必要，但最好是讓 P/Invoke 宣告成為實值類別的靜態成員，使其不存在於全域命名空間中，如下列範例所示。

```
// pinvoke_basic.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

value class Win32 {
public:
   [DllImport("User32.dll")]
   static int GetSystemMetrics(int);

   enum class SystemMetricIndex {
      // Same values as those defined in winuser.h.
      SM_CXSCREEN = 0,
      SM_CYSCREEN = 1
   };
};

int main() {
   int hRes = Win32::GetSystemMetrics( safe_cast<int>(Win32::SystemMetricIndex::SM_CXSCREEN) );
   int vRes = Win32::GetSystemMetrics( safe_cast<int>(Win32::SystemMetricIndex::SM_CYSCREEN) );
   Console::WriteLine("screen resolution: {0},{1}", hRes, vRes);
}
```

## <a name="see-also"></a>另請參閱

[在 C++ 中使用明確的 PInvoke (DllImport 屬性)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
