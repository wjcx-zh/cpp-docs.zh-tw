---
title: "使用 C++ Interop (隱含 PInvoke) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".NET [C++], 移植原生 C++ 至"
  - "Blittable 類型 [C++]"
  - "C++ COM Interop"
  - "C++ Interop"
  - "C++, Interop"
  - "COM 介面 [C++]"
  - "資料封送處理 [C++], C++ Interop 功能"
  - "範例 [C++], 互通性"
  - "隱含平台叫用"
  - "Interop [C++], 功能"
  - "互通性 [C++]"
  - "互通性 [C++], 隱含 PInvoke"
  - "封送處理 [C++], C++ Interop 功能"
  - "平台叫用 [C++], 範例"
  - "平台叫用 [C++], 隱含"
  - "移植 [C++], 原生 C++ 至 .NET"
  - "類型 [C++], Blittable"
ms.assetid: 5f710bf1-88ae-4c4e-8326-b3f0b7c4c68a
caps.latest.revision: 27
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用 C++ Interop (隱含 PInvoke)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

和其他的 .NET 語言不同，Visual C\+\+ 具有互通性 \(Interoperability\) 支援，允許 Managed 和 Unmanaged 程式碼存在於相同的應用程式，甚至是同一個檔案中 \(須使用 [managed、unmanaged](../preprocessor/managed-unmanaged.md) Pragma\)。  這樣 Visual C\+\+ 程式開發人員就可以將 .NET 功能整合至現有的 Visual C\+\+ 應用程式，不會影響到此應用程式的其他部分。  
  
 您也可以使用 [dllexport、dllimport](../cpp/dllexport-dllimport.md) 從 Managed 編譯單位 \(Compiland\) 呼叫 Unmanaged 函式。  
  
 隱含的 PInvoke 在您不需要指定封送處理函式參數的方式或明確呼叫 DllImportAttribute 時可指定之其他細節的時候很有用。  
  
 Visual C\+\+ 提供兩種方式，讓 Managed 和 Unmanaged 函式可以互通：  
  
-   [在 C\+\+ 中使用明確的 PInvoke \(DllImport 屬性\)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)  
  
 .NET Framework 支援明確的 PInvoke，並且可以在大多數的 .NET 語言中使用。  但是顧名思義，C\+\+ Interop 是 Visual C\+\+ 特有的。  
  
## C\+\+ Interop 的比較  
 比起明確的 PInvoke，更推薦您使用 C\+\+ Interop，因為可提供較佳的型別安全 \(Type Safety\)，實作起來比較有趣，較能容忍 Unmanaged API 的修改，並且可以加強效能 \(使用明確的 PInvoke 是做不到的\)。  然而，如果沒有 Unmanaged 原始程式碼或程式碼使用 **\/clr:safe** 編譯時 C\+\+ Interop 就無法使用 \(如需詳細資訊，請參閱[純粹的和可驗證的程式碼](../dotnet/pure-and-verifiable-code-cpp-cli.md)\)。  
  
## C\+\+ COM Interop  
 Visual C\+\+ 所支援的互通性功能，在與 COM 元件互通時可提供其他 .NET 語言所沒有的特別優點。  C\+\+ Interop 不受限於 .NET Framework [Tlbimp.exe \(Type Library Importer\)](../Topic/Tlbimp.exe%20\(Type%20Library%20Importer\).md) 的限制 \(例如對資料型別有限的支援，以及強制公開每個 COM 介面中每一個成員\)，它可以自由存取 COM 元件並且不需要額外的 Interop 組件。  如需詳細資訊，請參閱[Using COM from .NET](http://msdn.microsoft.com/zh-tw/03976661-6278-4227-a6c1-3b3315502c15)。  
  
## Blittable 型別  
 對於使用簡單內建型別 \(請參閱 [Blittable 和非 Blittable 類型](../Topic/Blittable%20and%20Non-Blittable%20Types.md)\) 的 Unmanaged API，您不需要特別撰寫程式碼，因為這些資料型別在記憶體中表示方式相同，但是更複雜的資料型別就需要明確的資料封送處理 \(Marshaling\)。  如需範例，請參閱 [如何：使用 PInvoke 從 Managed 程式碼呼叫原生 DLL](../dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke.md)。  
  
## 範例  
  
```  
// vcmcppv2_impl_dllimp.cpp  
// compile with: /clr:pure user32.lib  
using namespace System::Runtime::InteropServices;  
  
// Implicit DLLImport specifying calling convention  
extern "C" int __stdcall MessageBeep(int);  
  
// explicit DLLImport needed here to use P/Invoke marshalling because  
// System::String ^ is not the type of the first parameter to printf  
[DllImport("msvcrt.dll", EntryPoint = "printf", CallingConvention = CallingConvention::Cdecl,  CharSet = CharSet::Ansi)]  
// or just  
// [DllImport("msvcrt.dll")]  
int printf(System::String ^, ...);   
  
int main() {  
   // (string literals are System::String by default)  
   printf("Begin beep\n");  
   MessageBeep(100000);  
   printf("Done\n");  
}  
```  
  
  **開始嗶聲**  
**完成**   
## 本章節內容  
  
-   [如何：使用 C\+\+ Interop 封送處理 ANSI 字串](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)  
  
-   [如何：使用 C\+\+ Interop 封送處理 Unicode 字串](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)  
  
-   [如何：使用 C\+\+ Interop 封送處理 COM 字串](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)  
  
-   [如何：使用 C\+\+ Interop 封送處理結構](../dotnet/how-to-marshal-structures-using-cpp-interop.md)  
  
-   [如何：使用 C\+\+ Interop 封送處理陣列](../dotnet/how-to-marshal-arrays-using-cpp-interop.md)  
  
-   [如何：使用 C\+\+ Interop 封送處理回呼和委派](../dotnet/how-to-marshal-callbacks-and-delegates-by-using-cpp-interop.md)  
  
-   [如何：使用 C\+\+ Interop 封送處理內嵌指標](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md)  
  
-   [如何：存取 System::String 中的字元](../dotnet/how-to-access-characters-in-a-system-string.md)  
  
-   [如何：將 char \* 字串轉換為 System::Byte 陣列](../dotnet/how-to-convert-char-star-string-to-system-byte-array.md)  
  
-   [如何：將 System::String 轉換為 wchar\_t\* 或 char\*](../dotnet/how-to-convert-system-string-to-wchar-t-star-or-char-star.md)  
  
-   [如何：將 System::String 轉換為標準字串](../dotnet/how-to-convert-system-string-to-standard-string.md)  
  
-   [如何：將標準字串轉換為 System::String](../dotnet/how-to-convert-standard-string-to-system-string.md)  
  
-   [如何：取得位元組陣列的指標](../dotnet/how-to-obtain-a-pointer-to-byte-array.md)  
  
-   [如何：將 Unmanaged 資源載入至位元組陣列](../dotnet/how-to-load-unmanaged-resources-into-a-byte-array.md)  
  
-   [如何：修改原生函式中的參考類別](../dotnet/how-to-modify-reference-class-in-a-native-function.md)  
  
-   [如何：判斷影像是否為原生或 CLR](../dotnet/how-to-determine-if-an-image-is-native-or-clr.md)  
  
-   [如何：將原生 DLL 加入至全域組件快取](../dotnet/how-to-add-native-dll-to-global-assembly-cache.md)  
  
-   [如何：以原生類型存放實值類型的參考](../dotnet/how-to-hold-reference-to-value-type-in-native-type.md)  
  
-   [如何：在 Unmanaged 記憶體中存放物件參考](../dotnet/how-to-hold-object-reference-in-unmanaged-memory.md)  
  
-   [如何：偵測 \/clr 編譯](../dotnet/how-to-detect-clr-compilation.md)  
  
-   [如何：在 System::Guid 和 \_GUID 之間轉換](../dotnet/how-to-convert-between-system-guid-and-guid.md)  
  
-   [如何：指定 out 參數](../dotnet/how-to-specify-an-out-parameter.md)  
  
-   [如何：在 \/clr 編譯中使用原生類型](../dotnet/how-to-use-a-native-type-in-a-clr-compilation.md)  
  
-   [如何：以原生類型宣告控制代碼](../dotnet/how-to-declare-handles-in-native-types.md)  
  
-   [如何：包裝原生類別以便讓 C\# 使用](../dotnet/how-to-wrap-native-class-for-use-by-csharp.md)  
  
 如需在 Interop 案例中使用委派的詳細資訊，請參閱[delegate](../windows/delegate-cpp-component-extensions.md)。  
  
## 請參閱  
 [從 Managed 程式碼呼叫原生函式](../dotnet/calling-native-functions-from-managed-code.md)