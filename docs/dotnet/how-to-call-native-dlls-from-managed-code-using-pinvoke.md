---
title: 如何： 從 Managed 程式碼使用 PInvoke 呼叫原生 Dll |Microsoft 文件
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- platform invoke [C++], calling native DLLs
- interop [C++], calling native DLLs
- marshaling [C++], calling native DLLs
- data marshaling [C++], calling native DLLs
ms.assetid: 3273eb4b-38d1-4619-92a6-71bda542be72
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e82690e49daf324d0ff77f89710ecdd09b208c19
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33129183"
---
# <a name="how-to-call-native-dlls-from-managed-code-using-pinvoke"></a>如何：使用 PInvoke 從 Managed 程式碼呼叫原生 DLL
可以呼叫 unmanaged Dll 中實作的函式，從 managed 程式碼使用平台叫用 (P/Invoke) 的功能。 如果無法使用 DLL 的原始程式碼，P/Invoke 是互通的唯一選項。 不過，不同於其他.NET 語言中，Visual c + + 提供 P/Invoke 的替代方案。 如需詳細資訊，請參閱[使用 c + + Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)。  
  
## <a name="example"></a>範例  
 下列程式碼範例會使用 Win32 [GetSystemMetrics](http://msdn.microsoft.com/library/windows/desktop/ms724385)函式可擷取目前像素為單位的螢幕解析度。  
  
 對於僅使用內建類型當做引數和傳回值的函式，不不需要任何額外的工作。 其他資料類型，例如函式指標、 陣列和結構，需要額外的屬性，以確保適當的資料封送處理。  
  
 雖然並非必要，是很好的作法設 P/Invoke 宣告靜態成員的實值類別，好讓它們不在全域命名空間，如本範例所示。  
  
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