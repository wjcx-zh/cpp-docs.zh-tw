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
ms.openlocfilehash: d26fbefd87b3ba6d6ca7e183be78608777f383b5
ms.sourcegitcommit: 27d9db019f6d84c94de9e6aff0170d918cee6738
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2020
ms.locfileid: "75676926"
---
# <a name="using-c-interop-implicit-pinvoke"></a>使用 C++ Interop (隱含 PInvoke)

不同于其他 .NET 語言， C++視覺效果具有互通性支援，可讓受控和非受控程式碼存在於相同的應用程式中，甚至是在同一個檔案中（使用[受控、未受管理](../preprocessor/managed-unmanaged.md)的 pragma）。 這可讓C++視覺效果開發人員將 .net 功能整合C++到現有的視覺效果應用程式，而不會干擾應用程式的其餘部分。

您也可以使用[dllexport dllimport，](../cpp/dllexport-dllimport.md)從 managed 編譯模組呼叫非受控函式。

當您不需要指定如何封送處理函式參數，或在明確呼叫 DllImportAttribute 時指定的任何其他詳細資料時，隱含的 PInvoke 就很有用。

[ C++視覺效果] 提供兩種方式，讓 managed 和非受控函式相交互操作：

- [在 C++ 中使用明確的 PInvoke (DllImport 屬性)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)

明確的 PInvoke 受到 .NET Framework 的支援，而且在大部分的 .NET 語言中都有提供。 但正如其名， C++ Interop 是視覺效果C++特有的。

## <a name="c-interop"></a>C++ Interop

C++Interop 提供較佳的型別安全，而執行起來通常較不繁瑣。 不過， C++如果無法使用非受控原始程式碼或跨平臺專案，Interop 就不是選項。

## <a name="c-com-interop"></a>C++ COM Interop

視覺效果C++所支援的互通性功能，在與 COM 元件互通時，會提供與其他 .net 語言的特殊優勢。 Interop 不受限於 .NET Framework [tlbimp.exe （類型程式庫匯入工具）](/dotnet/framework/tools/tlbimp-exe-type-library-importer)的限制，例如有限的資料類型支援，以及每個 COM 介面之每個成員的強制性公開， C++ interop 可讓 COM 元件進行存取，而不需要個別的 Interop 元件。 不同于 Visual Basic C#和， C++ Visual 可以直接使用使用一般 Com 機制（例如**COCREATEINSTANCE**和**QueryInterface**）的 com 物件。 這是可能的， C++因為 Interop 功能會導致編譯器自動插入轉換程式碼，以便從 managed 移至非受控函式，然後再次返回。

使用C++ Interop 時，可以使用 COM 元件，因為它們通常會使用，也可以包裝在C++類別內。 這些包裝函式類別稱為「自訂執行時間可呼叫包裝函式」（CRCWs），而且在應用程式代碼中與直接使用 COM 相比有兩個優點：

- 產生的類別可以從視覺效果C++以外的語言使用。

- 您可以從 managed 用戶端程式代碼隱藏 COM 介面的詳細資料。 .NET 資料類型可以用來取代原生類型，而資料封送處理的細節則可以在 CRCW 內以透明的方式執行。

無論是直接使用 COM 或透過 CRCW，都必須封送處理簡單、可直接執行的引數類型。

## <a name="blittable-types"></a>可直接輸入的類型

針對使用簡單、內建類型的非受控 Api （請參閱可轉型[和非](/dotnet/framework/interop/blittable-and-non-blittable-types)類型的類型），不需要特殊程式碼，因為這些資料類型在記憶體中有相同的標記法，但更複雜的資料類型需要明確的資料封送處理。 如需範例，請參閱[如何：使用 PInvoke 從 Managed 程式碼呼叫原生 dll](../dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke.md)。

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

## <a name="in-this-section"></a>本章節內容

- [如何：使用 C++ Interop 封送處理 ANSI 字串](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)

- [如何：使用 C++ Interop 封送處理 Unicode 字串](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)

- [如何：使用 C++ Interop 封送處理 COM 字串](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)

- [如何：使用 C++ Interop 封送處理結構](../dotnet/how-to-marshal-structures-using-cpp-interop.md)

- [如何：使用 C++ Interop 封送處理陣列](../dotnet/how-to-marshal-arrays-using-cpp-interop.md)

- [如何：使用 C++ Interop 封送處理回呼和委派](../dotnet/how-to-marshal-callbacks-and-delegates-by-using-cpp-interop.md)

- [如何：使用 C++ Interop 封送處理內嵌指標](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md)

- [如何：存取 System::String 中的字元](../dotnet/how-to-access-characters-in-a-system-string.md)

- [如何：將 char * 字串轉換為 System::Byte 陣列](../dotnet/how-to-convert-char-star-string-to-system-byte-array.md)

- [如何：將 System：： String 轉換成 wchar_t * 或 char\*](../dotnet/how-to-convert-system-string-to-wchar-t-star-or-char-star.md)

- [如何：將 System::String 轉換為標準字串](../dotnet/how-to-convert-system-string-to-standard-string.md)

- [如何：將標準字串轉換為 System::String](../dotnet/how-to-convert-standard-string-to-system-string.md)

- [如何：取得位元組陣列的指標](../dotnet/how-to-obtain-a-pointer-to-byte-array.md)

- [如何：將 Unmanaged 資源載入至位元組陣列](../dotnet/how-to-load-unmanaged-resources-into-a-byte-array.md)

- [如何：修改原生函式中的參考類別](../dotnet/how-to-modify-reference-class-in-a-native-function.md)

- [如何：判斷影像是否為原生或 CLR](../dotnet/how-to-determine-if-an-image-is-native-or-clr.md)

- [如何：將原生 DLL 新增至全域組件快取](../dotnet/how-to-add-native-dll-to-global-assembly-cache.md)

- [如何：以原生類型存放實值型別的參考](../dotnet/how-to-hold-reference-to-value-type-in-native-type.md)

- [如何：在 Unmanaged 記憶體中存放物件參考](../dotnet/how-to-hold-object-reference-in-unmanaged-memory.md)

- [如何：偵測/clr 編譯](../dotnet/how-to-detect-clr-compilation.md)

- [如何：在 System::Guid 和 _GUID 之間轉換](../dotnet/how-to-convert-between-system-guid-and-guid.md)

- [如何：指定 out 參數](../dotnet/how-to-specify-an-out-parameter.md)

- [如何：在/clr 編譯中使用原生類型](../dotnet/how-to-use-a-native-type-in-a-clr-compilation.md)

- [如何：以原生類型宣告控制代碼](../dotnet/how-to-declare-handles-in-native-types.md)

- [如何：包裝原生類別以便讓 C# 使用](../dotnet/how-to-wrap-native-class-for-use-by-csharp.md)

如需在 interop 案例中使用委派的詳細資訊，請參閱[委派（C++元件擴充功能）](../extensions/delegate-cpp-component-extensions.md)。

## <a name="see-also"></a>請參閱

- [從 Managed 程式碼呼叫原生函式](../dotnet/calling-native-functions-from-managed-code.md)
