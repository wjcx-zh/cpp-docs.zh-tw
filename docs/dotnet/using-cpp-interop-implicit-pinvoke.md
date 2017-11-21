---
title: "使用 c + + Interop (隱含 PInvoke) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- blittable types [C++]
- platform invoke [C++], implicit
- interop [C++], features
- data marshaling [C++], C++ Interop features
- porting [C++], C++ native to .NET
- COM interfaces [C++]
- implicit platform invoke
- examples [C++], interoperability
- types [C++], blittable
- marshaling [C++], C++ Interop features
- platform invoke [C++], examples
- interoperability [C++]
- C++ Interop
- interoperability [C++], Implicit PInvoke
- C++, interop
- C++ COM Interop
- .NET [C++], porting C++ native to
ms.assetid: 5f710bf1-88ae-4c4e-8326-b3f0b7c4c68a
caps.latest.revision: "27"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1f400ed3e93af8f7e0727d3fe378d0ac471bd18f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="using-c-interop-implicit-pinvoke"></a>使用 C++ Interop (隱含 PInvoke)
不同於其他.NET 語言中，Visual c + + 已經在同一個應用程式，甚至相同的檔案，可讓存在於 managed 和 unmanaged 程式碼的互通性支援 (使用[managed、 unmanaged](../preprocessor/managed-unmanaged.md) pragma)。 這可讓 Visual c + + 開發人員整合至現有的 Visual c + + 應用程式的.NET 功能，也不會干擾其餘的應用程式。  
  
 您也可以呼叫 unmanaged 函式，從受管理的編譯模組使用[dllexport、 dllimport](../cpp/dllexport-dllimport.md)。  
  
 隱含 PInvoke 時，您不需要指定如何函式參數會封送處理，或任何其他明確呼叫 DllImportAttribute 時，可以指定的詳細資料。  
  
 Visual c + + 提供交互操作的 managed 和 unmanaged 函式的兩種方式：  
  
-   [在 C++ 中使用明確的 PInvoke (DllImport 屬性)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)  
  
 明確的 PInvoke.NET Framework 所支援，可在大部分的.NET 語言。 但是，正如其名，是 Visual c + + 特有的 c + + Interop。  
  
## <a name="c-interop"></a>C++ Interop  
 C + + Interop 建議透過明確的 PInvoke 因為它提供更佳的型別安全實作通常較不費時，為時更寬容 unmanaged 的 API 已經過修改，並讓效能增強功能可能就無法使用，明確PInvoke。 不過，c + + Interop 不可能或如果無法使用未受管理的來源程式碼編譯時**/clr: safe**。 **/clr:pure** 和 **/clr:safe** 編譯器選項在 Visual Studio 2015 中已被取代。 如需資訊，請參閱[純粹的和可驗證程式碼 (C + + /CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)。  
  
## <a name="c-com-interop"></a>C++ COM Interop  
 與 COM 元件相互操作時，支援 Visual c + + 的互通性功能會提供其他.NET 語言特定的優勢。 而不是以.NET framework 限制受限於[Tlbimp.exe （類型程式庫匯入工具）](/dotnet/framework/tools/tlbimp-exe-type-library-importer)，例如有限支援資料類型，以及強制公開的每個 COM 介面的每個成員，c + + Interop 允許 COM要在存取元件將而且不需要個別的 interop 組件。 如需詳細資訊，請參閱[使用 COM 從.NET](http://msdn.microsoft.com/en-us/03976661-6278-4227-a6c1-3b3315502c15)。  
  
## <a name="blittable-types"></a>Blittable 類型  
 使用簡單、 內建類型的 unmanaged api (請參閱[Blittable 和非 Blittable 類型](http://msdn.microsoft.com/Library/d03b050e-2916-49a0-99ba-f19316e5c1b3))，因為這些資料型別都具有相同表示在記憶體中，但更複雜的資料類型需要任何特殊的程式碼為必要明確的資料封送處理。 如需範例，請參閱[How to： 從 Managed 程式碼使用 PInvoke 呼叫原生 Dll](../dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke.md)。  
  
## <a name="example"></a>範例  
  
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
  
```Output  
Begin beep  
Done  
```  
  
## <a name="in-this-section"></a>本章節內容  
  
-   [如何：使用 C++ Interop 封送處理 ANSI 字串](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)  
  
-   [如何：使用 C++ Interop 封送處理 Unicode 字串](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)  
  
-   [如何：使用 C++ Interop 封送處理 COM 字串](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)  
  
-   [如何：使用 C++ Interop 封送處理結構](../dotnet/how-to-marshal-structures-using-cpp-interop.md)  
  
-   [如何：使用 C++ Interop 封送處理陣列](../dotnet/how-to-marshal-arrays-using-cpp-interop.md)  
  
-   [如何：使用 C++ Interop 封送處理回呼和委派](../dotnet/how-to-marshal-callbacks-and-delegates-by-using-cpp-interop.md)  
  
-   [如何：使用 C++ Interop 封送處理內嵌指標](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md)  
  
-   [如何：存取 System::String 中的字元](../dotnet/how-to-access-characters-in-a-system-string.md)  
  
-   [如何：將 char * 字串轉換為 System::Byte 陣列](../dotnet/how-to-convert-char-star-string-to-system-byte-array.md)  
  
-   [如何： 將 system:: string 轉換為 wchar_t * 或 char\*](../dotnet/how-to-convert-system-string-to-wchar-t-star-or-char-star.md)  
  
-   [如何：將 System::String 轉換為標準字串](../dotnet/how-to-convert-system-string-to-standard-string.md)  
  
-   [如何：將標準字串轉換為 System::String](../dotnet/how-to-convert-standard-string-to-system-string.md)  
  
-   [如何：取得位元組陣列的指標](../dotnet/how-to-obtain-a-pointer-to-byte-array.md)  
  
-   [如何：將 Unmanaged 資源載入至位元組陣列](../dotnet/how-to-load-unmanaged-resources-into-a-byte-array.md)  
  
-   [如何：修改原生函式中的參考類別](../dotnet/how-to-modify-reference-class-in-a-native-function.md)  
  
-   [如何：判斷影像是否為原生或 CLR](../dotnet/how-to-determine-if-an-image-is-native-or-clr.md)  
  
-   [如何：將原生 DLL 新增至全域組件快取](../dotnet/how-to-add-native-dll-to-global-assembly-cache.md)  
  
-   [如何：以原生類型存放實值型別的參考](../dotnet/how-to-hold-reference-to-value-type-in-native-type.md)  
  
-   [如何：在 Unmanaged 記憶體中存放物件參考](../dotnet/how-to-hold-object-reference-in-unmanaged-memory.md)  
  
-   [如何： 偵測 /clr 編譯](../dotnet/how-to-detect-clr-compilation.md)  
  
-   [如何：在 System::Guid 和 _GUID 之間轉換](../dotnet/how-to-convert-between-system-guid-and-guid.md)  
  
-   [如何：指定 out 參數](../dotnet/how-to-specify-an-out-parameter.md)  
  
-   [如何： 在 /clr 編譯中使用原生類型](../dotnet/how-to-use-a-native-type-in-a-clr-compilation.md)  
  
-   [如何：以原生類型宣告控制代碼](../dotnet/how-to-declare-handles-in-native-types.md)  
  
-   [如何：包裝原生類別以便讓 C# 使用](../dotnet/how-to-wrap-native-class-for-use-by-csharp.md)  
  
 如需在 interop 案例中使用委派資訊，請參閱[委派 （c + + 元件擴充功能）](../windows/delegate-cpp-component-extensions.md)。  
  
## <a name="see-also"></a>另請參閱  
 [從 Managed 程式碼呼叫原生函式](../dotnet/calling-native-functions-from-managed-code.md)