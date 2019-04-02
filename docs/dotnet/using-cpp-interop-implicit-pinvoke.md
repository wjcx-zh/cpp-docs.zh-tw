---
title: 使用 C++ Interop (隱含 PInvoke)
ms.date: 11/04/2016
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
ms.openlocfilehash: aaa07373b7dd22807290ceefa9197b4013c61fe5
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58778230"
---
# <a name="using-c-interop-implicit-pinvoke"></a>使用 C++ Interop (隱含 PInvoke)

不同於其他.NET 語言，Visual c + + 有互通性支援，可讓 managed 和 unmanaged 程式碼存在，在相同的應用程式，並甚至在相同的檔案 (使用[managed、 unmanaged](../preprocessor/managed-unmanaged.md) pragma)。 這可讓 Visual c + + 開發人員將.NET 功能整合到現有的 Visual c + + 應用程式中，而不會影響應用程式的其餘部分。

您也可以從受管理的編譯模組，使用呼叫 unmanaged 函式[dllexport、 dllimport](../cpp/dllexport-dllimport.md)。

隱含 PInvoke 時，您不需要指定如何函式參數會封送處理，或任何其他明確呼叫 DllImportAttribute 時，可以指定的詳細資料。

Visual c + + 提供兩種方法讓交互操作的 managed 和 unmanaged 函式：

- [在 C++ 中使用明確的 PInvoke (DllImport 屬性)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)

明確的 PInvoke 支援的.NET Framework，並且可在大部分的.NET 語言。 但是，正如其名，c + + Interop 是特定 Visual c + +。

## <a name="c-interop"></a>C++ Interop

因為它提供更好的型別安全實作通常比較不瑣碎，如果未受管理的 API 已經過修改，而使效能增強功能可能即無法在明確是更寬容明確的 PInvoke 建議 c + + InteropPInvoke。 不過，c + + Interop 不可能，如果無法使用未受管理的原始程式碼。

## <a name="c-com-interop"></a>C++ COM Interop

與 COM 元件交互操作時，支援的 Visual c + + 的互通性功能會提供優於其他.NET 語言的特定優點。 而不受限於.NET Framework 的限制[Tlbimp.exe （型別程式庫匯入工具）](/dotnet/framework/tools/tlbimp-exe-type-library-importer)，限制對資料型別和必要的曝光度的每個 COM 介面的每個成員的詳細資訊，例如 c + + Interop 讓 COM若要在存取元件將而且不需要個別的 interop 組件。 不同於 Visual Basic 和C#，Visual c + + 可以使用直接使用一般的 COM 機制的 COM 物件 (例如**CoCreateInstance**並**QueryInterface**)。 這是可能會因為 c + + Interop 功能，會導致編譯器自動插入的轉換程式碼，以從 managed 到 unmanaged 的函式及移動一次。

使用 c + + Interop，COM 元件便能以一般使用，或在 c + + 類別包裝起來。 這些包裝函式的類別稱為自訂執行階段可呼叫包裝函式，或 CRCWs，而且它們有透過直接在應用程式程式碼中使用 COM 的兩個優點：

- 產生的類別可以從 Visual c + + 以外的語言使用。

- 從受管理的用戶端程式碼，可以隱藏 COM 介面的詳細資料。 .NET 資料型別可以用來取代原生類型，並可以無障礙地執行資料封送處理的詳細資料，CRCW 內。

不論是否直接或透過 CRCW，使用 COM，簡單的 blittable 類型以外的引數類型必須是封送處理。

## <a name="blittable-types"></a>Blittable 類型

使用簡單、 內建類型的 unmanaged api (請參閱[Blittable 和非 Blittable 類型](/dotnet/framework/interop/blittable-and-non-blittable-types))，因為這些資料類型都有相同表示法在記憶體中，但更複雜的資料類型需要任何特殊的程式碼是必要明確封送處理的資料。 如需範例，請參閱[如何：從使用 PInvoke 的 Managed 程式碼呼叫原生 Dll](../dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke.md)。

## <a name="example"></a>範例

```cpp
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

## <a name="in-this-section"></a>本節內容

- [如何：使用 C++ Interop 封送處理 ANSI 字串](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)

- [如何：使用 C++ Interop 封送處理 Unicode 字串](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)

- [如何：使用 C++ Interop 封送處理 COM 字串](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)

- [如何：使用 C++ Interop 封送處理結構](../dotnet/how-to-marshal-structures-using-cpp-interop.md)

- [如何：使用 C++ Interop 封送處理陣列](../dotnet/how-to-marshal-arrays-using-cpp-interop.md)

- [如何：使用 C++ Interop 封送處理回呼和委派](../dotnet/how-to-marshal-callbacks-and-delegates-by-using-cpp-interop.md)

- [如何：使用 C++ Interop 封送處理內嵌指標](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md)

- [如何：存取 System::String 中的字元](../dotnet/how-to-access-characters-in-a-system-string.md)

- [如何：將 char * 字串轉換為 System::Byte 陣列](../dotnet/how-to-convert-char-star-string-to-system-byte-array.md)

- [如何：將 system:: string 轉換為 wchar_t * 或 char\*](../dotnet/how-to-convert-system-string-to-wchar-t-star-or-char-star.md)

- [如何：將 System::String 轉換為標準字串](../dotnet/how-to-convert-system-string-to-standard-string.md)

- [如何：將標準字串轉換為 System::String](../dotnet/how-to-convert-standard-string-to-system-string.md)

- [如何：取得位元組陣列的指標](../dotnet/how-to-obtain-a-pointer-to-byte-array.md)

- [如何：將非受控資源載入至位元組陣列](../dotnet/how-to-load-unmanaged-resources-into-a-byte-array.md)

- [如何：修改原生函式中的參考類別](../dotnet/how-to-modify-reference-class-in-a-native-function.md)

- [如何：判斷影像為原生或 CLR](../dotnet/how-to-determine-if-an-image-is-native-or-clr.md)

- [如何：將原生 DLL 新增至全域組件快取](../dotnet/how-to-add-native-dll-to-global-assembly-cache.md)

- [如何：以原生類型存放實值型別的參考](../dotnet/how-to-hold-reference-to-value-type-in-native-type.md)

- [如何：在非受控記憶體中存放物件參考](../dotnet/how-to-hold-object-reference-in-unmanaged-memory.md)

- [如何：偵測 /clr 編譯](../dotnet/how-to-detect-clr-compilation.md)

- [如何：在 System::Guid 和 _GUID 之間轉換](../dotnet/how-to-convert-between-system-guid-and-guid.md)

- [如何：指定 out 參數](../dotnet/how-to-specify-an-out-parameter.md)

- [如何：在 /clr 編譯中使用原生類型](../dotnet/how-to-use-a-native-type-in-a-clr-compilation.md)

- [如何：以原生類型宣告控制代碼](../dotnet/how-to-declare-handles-in-native-types.md)

- [如何：包裝原生類別以便讓 C# 使用](../dotnet/how-to-wrap-native-class-for-use-by-csharp.md)

如需在 interop 的案例中使用委派的資訊，請參閱[委派 （c + + 元件延伸模組）](../extensions/delegate-cpp-component-extensions.md)。

## <a name="see-also"></a>另請參閱

- [從 Managed 程式碼呼叫原生函式](../dotnet/calling-native-functions-from-managed-code.md)
