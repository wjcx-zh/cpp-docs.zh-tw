---
title: "如何：使用 PInvoke 從 Managed 程式碼呼叫原生 DLL | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "資料封送處理 [C++], 呼叫原生 DLL"
  - "Interop [C++], 呼叫原生 DLL"
  - "封送處理 [C++], 呼叫原生 DLL"
  - "平台叫用 [C++], 呼叫原生 DLL"
ms.assetid: 3273eb4b-38d1-4619-92a6-71bda542be72
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用 PInvoke 從 Managed 程式碼呼叫原生 DLL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以使用平台叫用 \(P\/Invoke\) 功能從 Managed 程式碼中呼叫實作在 Unmanaged DLL 中的函式。  如果沒有 DLL 的原始程式碼，則 P\/Invoke 是互通的唯一選擇。  不過，不同於其他 .NET 語言，Visual C\+\+ 提供了 P\/Invoke 的替代方案。  如需詳細資訊，請參閱[使用 C\+\+ Interop \(隱含 PInvoke\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)。  
  
## 範例  
 下列程式碼範例會使用 Win32 [GetSystemMetrics](http://msdn.microsoft.com/library/windows/desktop/ms724385) 函式，擷取目前的螢幕解析度 \(以像素為單位\)。  
  
 對於只使用內建 \(Intrinsic\) 型別做為引數和傳回值的函式，則不需要執行其他工作。  其他資料型別 \(例如函式指標、陣列和結構\) 會需要額外的屬性，以確保資料封送處理 \(Marshaling\) 作業可以正確執行。  
  
 雖然不是必要步驟，但是將 P\/Invoke 宣告設定成某個實值類別的靜態成員，使這些宣告不會出現在全域命名空間 \(如本範例所示\)，是個很好的做法。  
  
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
  
## 請參閱  
 [在 C\+\+ 中使用明確的 PInvoke \(DllImport 屬性\)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)