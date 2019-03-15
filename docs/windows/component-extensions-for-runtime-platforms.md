---
title: 適用於.NET 和 UWP 的元件擴充功能
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- what's new [C++], keywords
- what's new [C++], language features
- C++, keywords
- keywords [C++]
- Managed Extensions for C++, replacement syntax
ms.assetid: 1e400ee6-3ac9-4910-a608-9d3d5993e423
ms.openlocfilehash: e9586244c9e2293ba6b484efb158fc3a2529c0ea
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2019
ms.locfileid: "57814484"
---
# <a name="component-extensions-for-net-and-uwp"></a>適用於.NET 和 UWP 的元件擴充功能

C + + 標準，可讓編譯器廠商，提供非標準的語言擴充功能。 Microsoft 提供擴充功能，協助您連接的原生 c + + 程式碼程式碼，在.NET Framework 或通用 Windows 平台 (UWP) 上執行。 .NET 延伸模組會呼叫 C + +.NET 中執行的 CLI 和產生的程式碼管理稱為 Common Language Runtime (CLR) 的執行環境。 UWP 延伸模組會呼叫 C + + /CX 和它們產生原生機器碼。

> [!NOTE]
> 對於新的應用程式，我們建議使用 C + + /cli WinRT 而不是 C + + /CX。 C + + /cli WinRT 是新的標準 C + + 17 語言推演，適用於 Windows 執行階段 Api。 我們會繼續支援 C + + /CX 和 WRL，但強烈建議新的應用程式使用 C + + /cli WinRT。 如需詳細資訊，請參閱 < [C + + /cli WinRT](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/index)。

### <a name="two-runtimes-one-set-of-extensions"></a>兩種執行階段，一組擴充功能

C + + /cli CLI 延伸 ISO/ANSI c + + 標準，並定義在 Ecma C + + /cli CLI 標準。 如需詳細資訊，請參閱 < [.NET 程式設計使用 C + + /cli （Visual c + +）](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)。

C + + /CX 延伸模組是子集的 C + + /cli CLI。 雖然延伸語法完全相同，在大部分情況下，產生的程式碼取決於您是否指定`/ZW`編譯器選項，目標 UWP 或`/clr`以.NET 為目標的選項。 當您使用 Visual Studio 以建立專案時，會自動設定這些參數。

## <a name="data-type-keywords"></a>資料類型關鍵字

語言擴充功能包含*彙總關鍵字*，其中包含以泛空白字元分隔的兩個語彙基元。 當語彙基元分開使用時，可能有一個意義，當它們一起使用時，則有另一個意義。 例如，"ref" 這個字是一般的識別項，而 "class" 這個字是宣告原生類別的關鍵字。 但當這些字合併以形成**ref 類別**，產生的彙總關鍵字會宣告稱為實體*執行階段類別*。

擴充功能也包括*即時線上*關鍵字。 關鍵字會被視為視內容而有所區別，取決於包含它的陳述式類型，以及它在該陳述式中的位置。 例如，語彙基元 "property" 可以是識別碼，或者它可以宣告一種特殊的公用類別成員。

下表列出在 C++ 語言擴充功能中的關鍵字。

|關鍵字|視內容而有所區別|用途|參考資料|
|-------------|-----------------------|-------------|---------------|
|**ref 類別**<br /><br /> **ref 結構**|否|宣告類型。|[類別和結構](../windows/classes-and-structs-cpp-component-extensions.md)|
|**實值類別**<br /><br /> **實值結構**|否|宣告值類型。|[類別和結構](../windows/classes-and-structs-cpp-component-extensions.md)|
|**介面類別**<br /><br /> **介面結構**|否|宣告介面。|[介面類別](../windows/interface-class-cpp-component-extensions.md)|
|**列舉類別**<br /><br /> **列舉結構**|否|宣告列舉。|[列舉類別](../windows/enum-class-cpp-component-extensions.md)|
|**屬性**|是|宣告屬性。|[屬性](../windows/property-cpp-component-extensions.md)|
|**delegate**|是|宣告委派。|[委派  (C++/CLI 和 C++/CX)](../windows/delegate-cpp-component-extensions.md)|
|**event**|是|宣告事件。|[event](../windows/event-cpp-component-extensions.md)|

## <a name="override-specifiers"></a>覆寫規範

您可以使用下列關鍵字限定衍生的覆寫行為。 雖然**新**關鍵字無效的 c + + 延伸模組，它列在這裡，因為它可以用於其他內容。 某些規範對於原生程式設計也有效。 如需詳細資訊，請參閱[如何：宣告在原生編譯中的覆寫規範 (C + + /cli CLI)](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)。

|關鍵字|視內容而有所區別|用途|參考資料|
|-------------|-----------------------|-------------|---------------|
|**abstract**|是|表示函式或類別為抽象。|[abstract](../windows/abstract-cpp-component-extensions.md)|
|**new**|否|表示函式不是基底類別版本的覆寫。|[new （新位置 vtable 中）](../windows/new-new-slot-in-vtable-cpp-component-extensions.md)|
|**override**|是|表示方法必須是基底類別版本的覆寫。|[override](../windows/override-cpp-component-extensions.md)|
|**sealed**|是|避免將類別做為基底類別。|[sealed](../windows/sealed-cpp-component-extensions.md)|

## <a name="keywords-for-generics"></a>泛型的關鍵字

下列關鍵字已加入以支援泛型類型。 如需詳細資訊，請參閱[泛型](../windows/generics-cpp-component-extensions.md)。

|關鍵字|視內容而有所區別|用途|
|-------------|-----------------------|-------------|
|**generic**|否|宣告泛型類型。|
|**where**|是|指定套用至泛型類型參數的條件約束。|

## <a name="miscellaneous-keywords"></a>其他關鍵字

下列關鍵字已加入至 C++ 擴充功能。

|關鍵字|視內容而有所區別|用途|參考資料|
|-------------|-----------------------|-------------|---------------|
|**finally**|是|表示預設例外狀況處理行為。|[例外狀況處理](../windows/exception-handling-cpp-component-extensions.md)|
|**for each, in**|否|列舉集合的項目。|[for each, in](../dotnet/for-each-in.md)|
|**gcnew**|否|在記憶體回收堆積上配置類型。 而不是使用**新**並**刪除**。|[ref new 和 gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md)|
|**新的 ref**|是|配置是 Windows 執行階段類型。 而不是使用**新**並**刪除**。|[ref new 和 gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md)|
|**initonly**|是|表示成員只能在宣告或靜態建構函式中初始化。|[initonly (C++/CLI)](../dotnet/initonly-cpp-cli.md)|
|**名稱**|是|建立常值變數。|[名稱](../windows/literal-cpp-component-extensions.md)|
|**nullptr**|否|指出控制代碼或指標未指向物件。|[nullptr](../windows/nullptr-cpp-component-extensions.md)|

## <a name="template-constructs"></a>範本建構

下列語言建構會實作為範本，而不是關鍵字。 如果您指定 `/ZW` 編譯器選項，則它們會在 `lang` 命名空間中定義。 如果您指定 `/clr` 編譯器選項，則它們會在 `cli` 命名空間中定義。

|關鍵字|用途|參考資料|
|-------------|-------------|---------------|
|**array**|宣告陣列。|[陣列](../windows/arrays-cpp-component-extensions.md)|
|**interior_ptr**|(只有 CLR) 指向參考類型中的資料。|[interior_ptr (C++/CLI)](../windows/interior-ptr-cpp-cli.md)|
|**pin_ptr**|(只有 CLR) 指向 CLR 參考類型以暫時隱藏記憶體回收系統。|[pin_ptr (C++/CLI)](../windows/pin-ptr-cpp-cli.md)|
|**safe_cast**|決定並執行執行階段類型的最佳轉型方法。|[safe_cast](../windows/safe-cast-cpp-component-extensions.md)|
|**typeid**|(只有 CLR) 擷取 <xref:System.Type?displayProperty=fullName> 物件，該物件描述指定類型或物件。|[typeid](../windows/typeid-cpp-component-extensions.md)|

## <a name="declarators"></a>宣告子

下列類型宣告子會指示執行階段自動管理配置物件的存留期和刪除。

|運算子|用途|參考資料|
|--------------|-------------|---------------|
|`^`|宣告物件的控制代碼也就是會自動刪除時不再使用舊的 Windows 執行階段或 CLR 物件的指標。|[物件控制代碼運算子 (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)|
|`%`|宣告追蹤參考;也就是會自動刪除時不再使用舊的 Windows 執行階段或 CLR 物件的參考。|[追蹤參考運算子](../windows/tracking-reference-operator-cpp-component-extensions.md)|

## <a name="additional-constructs-and-related-topics"></a>其他建構和相關主題

本節列出與 CLR 有關的其他程式設計建構和主題。

|主題|描述|
|-----------|-----------------|
|[__identifier (C++/CLI)](../windows/identifier-cpp-cli.md)|（Windows 執行階段和 CLR）啟用使用的關鍵字當做識別項。|
|[變數引數清單 (...) (C++/CLI)](../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md)|（Windows 執行階段和 CLR）可讓函式接受可變數目的引數。|
|[C++ 原生類型的 .NET Framework 對等項 (C++/CLI)](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md)|列出用來取代 C++ 整數類型的 CLR 類型。|
|[appdomain](../cpp/appdomain.md) **__declspec** modifier|**__declspec**修飾詞，要求每個 appdomain 都有靜態和全域變數。|
|[使用 /clr 進行 C-style 轉換 (C + + /cli CLI)](../windows/c-style-casts-with-clr-cpp-cli.md)|描述 C-style 轉換的解譯方式。|
|[__clrcall](../cpp/clrcall.md)呼叫慣例|表示 CLR 相容的呼叫慣例。|
|`__cplusplus_cli`|[預先定義的巨集](../preprocessor/predefined-macros.md)|
|[自訂屬性](../windows/custom-attributes-cpp.md)|描述如何定義您自己的 CLR 屬性。|
|[例外狀況處理](../windows/exception-handling-cpp-component-extensions.md)|提供例外狀況處理的概觀。|
|[明確覆寫](../windows/explicit-overrides-cpp-component-extensions.md)|示範成員函式如何覆寫任意成員。|
|[Friend 組件 (C++)](../dotnet/friend-assemblies-cpp.md)|討論用戶端組件如何存取組件元件中的所有類型。|
|[Boxing](../windows/boxing-cpp-component-extensions.md)|示範 boxed 處理值類型的條件。|
|[類型特性的編譯器支援](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)|討論如何在編譯時偵測類型的特性。|
|[managed、 unmanaged](../preprocessor/managed-unmanaged.md) pragma|示範 Managed 和 Unmanaged 函式如何共存於相同的模組。|
|[process](../cpp/process.md) **__declspec** modifier|**__declspec**修飾詞，要求每個處理序都有靜態和全域變數。|
|[反映 (C++/CLI)](../dotnet/reflection-cpp-cli.md)|示範執行階段類型資訊的 CLR 版本。|
|[String](../windows/string-cpp-component-extensions.md)|討論字串常值到 <xref:System.String> 的編譯器轉換。|
|[類型轉送 (C++/CLI)](../windows/type-forwarding-cpp-cli.md)|在傳送組件中讓類型移動到另一個組件，讓用戶端程式碼不需要重新編譯。|
|[使用者定義的屬性](../windows/user-defined-attributes-cpp-component-extensions.md)|示範使用者定義屬性。|
|[#using 指示詞](../preprocessor/hash-using-directive-cpp.md)|匯入外部組件。|
|[XML 文件](../build/reference/xml-documentation-visual-cpp.md)|說明以 XML 為基礎的程式碼文件使用[/doc （處理文件註解） （C/c + +）](../build/reference/doc-process-documentation-comments-c-cpp.md)|

## <a name="see-also"></a>另請參閱

[以 C++/CLI 進行 .NET 程式設計 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br/>
[原生和 .NET 互通性](../dotnet/native-and-dotnet-interoperability.md)