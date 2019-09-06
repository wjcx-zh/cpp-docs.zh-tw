---
title: 適用於 .NET 與 UWP 的元件擴充功能
ms.date: 10/12/2018
ms.topic: landing-page
helpviewer_keywords:
- what's new [C++], keywords
- what's new [C++], language features
- C++, keywords
- keywords [C++]
- Managed Extensions for C++, replacement syntax
ms.assetid: 1e400ee6-3ac9-4910-a608-9d3d5993e423
ms.openlocfilehash: 76cbb20d108745984490e67b53db39f58e34d327
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70311758"
---
# <a name="component-extensions-for-net-and-uwp"></a>適用於 .NET 與 UWP 的元件擴充功能

C++ 標準讓編譯器廠商能夠為此語言提供非標準的擴充功能。 Microsoft 提供擴充功能，可協助您將 C++ 機器碼連線至在 .NET Framework 或通用 Windows 平台 (UWP) 上執行的程式碼。 .NET 擴充功能稱為 C++/CLI，並會產生要在稱為 Common Language Runtime (CLR) 的 .NET 受控執行環境中執行的程式碼。 UWP 擴充功能稱為 C++/CX，而它們會產生原生機器碼。

> [!NOTE]
> 對於新的應用程式，我們建議使用 C++/WinRT 而不是 C++/CX。 C++/WinRT 是適用於 Windows 執行階段 API 的新標準 C++17 語言投影。 我們將繼續支援 C++/CX 和 WRL，但強烈建議讓新的應用程式使用 C++/WinRT。 如需詳細資訊，請參閱 [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/index)。

### <a name="two-runtimes-one-set-of-extensions"></a>兩種執行階段，一組擴充功能

C++/CLI 會擴充 ISO/ANSI C++ 標準，並根據 Ecma C++/CLI 標準來定義。 如需詳細資訊，請參閱[以 C++/CLI 進行 .NET 程式設計 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)。

C++/CX 擴充功能為 C++/CLI 的子集。 雖然在大部分情況下擴充功能語法會完全相同，但產生的程式碼取決於您是否指定 `/ZW` 編譯器選項以將目標設定為 UWP，或指定 `/clr` 選項以將目標設定為 .NET。 當您使用 Visual Studio 以建立專案時，會自動設定這些參數。

## <a name="data-type-keywords"></a>資料類型關鍵字

語言擴充功能包含「彙總關鍵字」，這類關鍵字會由空白字元分隔的兩個語彙基元所組成。 當語彙基元分開使用時，可能有一個意義，當它們一起使用時，則有另一個意義。 例如，"ref" 這個字是一般的識別項，而 "class" 這個字是宣告原生類別的關鍵字。 但是，當這些字組合併以形成 **ref class** 時，產生的彙總關鍵字會宣告實體，也就是「執行階段類別」。

擴充功能也包括「內容關鍵性」關鍵字。 關鍵字會被視為視內容而有所區別，取決於包含它的陳述式類型，以及它在該陳述式中的位置。 例如，語彙基元 "property" 可以是識別碼，或者它可以宣告一種特殊的公用類別成員。

下表列出在 C++ 語言擴充功能中的關鍵字。

|關鍵字|視內容而有所區別|用途|參考資料|
|-------------|-----------------------|-------------|---------------|
|**ref class**<br /><br /> **ref struct**|否|宣告類型。|[類別和結構](classes-and-structs-cpp-component-extensions.md)|
|**value class**<br /><br /> **value struct**|否|宣告值類型。|[類別和結構](classes-and-structs-cpp-component-extensions.md)|
|**介面類別**<br /><br /> **interface struct**|否|宣告介面。|[介面類別](interface-class-cpp-component-extensions.md)|
|**enum 類別**<br /><br /> **enum struct**|否|宣告列舉。|[enum 類別](enum-class-cpp-component-extensions.md)|
|**屬性**|是|宣告屬性。|[屬性](property-cpp-component-extensions.md)|
|**delegate**|是|宣告委派。|[委派  (C++/CLI 和 C++/CX)](delegate-cpp-component-extensions.md)|
|**event**|是|宣告事件。|[event](event-cpp-component-extensions.md)|

## <a name="override-specifiers"></a>覆寫規範

您可以使用下列關鍵字限定衍生的覆寫行為。 雖然 **new** 關鍵字不是 C++ 的擴充功能，但將它列在這裡是因為可在其他內容中使用它。 某些規範對於原生程式設計也有效。 如需詳細資訊，請參閱[如何：在原生編譯中宣告覆寫指定名稱 (C++/CLI)](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)。

|關鍵字|視內容而有所區別|用途|參考資料|
|-------------|-----------------------|-------------|---------------|
|**abstract**|是|表示函式或類別為抽象。|[abstract](abstract-cpp-component-extensions.md)|
|**new**|否|表示函式不是基底類別版本的覆寫。|[new (vtable 中的新位置)](new-new-slot-in-vtable-cpp-component-extensions.md)|
|**override**|是|表示方法必須是基底類別版本的覆寫。|[override](override-cpp-component-extensions.md)|
|**sealed**|是|避免將類別做為基底類別。|[sealed](sealed-cpp-component-extensions.md)|

## <a name="keywords-for-generics"></a>泛型的關鍵字

下列關鍵字已加入以支援泛型類型。 如需詳細資訊，請參閱[泛型](generics-cpp-component-extensions.md)。

|關鍵字|視內容而有所區別|用途|
|-------------|-----------------------|-------------|
|**generic**|否|宣告泛型類型。|
|**where**|是|指定套用至泛型類型參數的條件約束。|

## <a name="miscellaneous-keywords"></a>其他關鍵字

下列關鍵字已加入至 C++ 擴充功能。

|關鍵字|視內容而有所區別|用途|參考資料|
|-------------|-----------------------|-------------|---------------|
|**finally**|是|表示預設例外狀況處理行為。|[例外狀況處理](exception-handling-cpp-component-extensions.md)|
|**for each, in**|否|列舉集合的項目。|[for each, in](../dotnet/for-each-in.md)|
|**gcnew**|否|在記憶體回收堆積上配置類型。 不使用 **new** 和 **delete**，改用此關鍵字。|[ref new、gcnew](ref-new-gcnew-cpp-component-extensions.md)|
|**ref new**|是|配置 Windows 執行階段型別。 不使用 **new** 和 **delete**，改用此關鍵字。|[ref new、gcnew](ref-new-gcnew-cpp-component-extensions.md)|
|**initonly**|是|表示成員只能在宣告或靜態建構函式中初始化。|[initonly (C++/CLI)](../dotnet/initonly-cpp-cli.md)|
|**名稱**|是|建立常值變數。|[名稱](literal-cpp-component-extensions.md)|
|**nullptr**|否|指出控制代碼或指標未指向物件。|[nullptr](nullptr-cpp-component-extensions.md)|

## <a name="template-constructs"></a>範本建構

下列語言建構會實作為範本，而不是關鍵字。 如果您指定 `/ZW` 編譯器選項，則它們會在 `lang` 命名空間中定義。 如果您指定 `/clr` 編譯器選項，則它們會在 `cli` 命名空間中定義。

|關鍵字|用途|參考資料|
|-------------|-------------|---------------|
|**array**|宣告陣列。|[陣列](arrays-cpp-component-extensions.md)|
|**interior_ptr**|(只有 CLR) 指向參考類型中的資料。|[interior_ptr (C++/CLI)](interior-ptr-cpp-cli.md)|
|**pin_ptr**|(只有 CLR) 指向 CLR 參考類型以暫時隱藏記憶體回收系統。|[pin_ptr (C++/CLI)](pin-ptr-cpp-cli.md)|
|**safe_cast**|決定並執行執行階段類型的最佳轉型方法。|[safe_cast](safe-cast-cpp-component-extensions.md)|
|**typeid**|(只有 CLR) 擷取 <xref:System.Type?displayProperty=fullName> 物件，該物件描述指定類型或物件。|[typeid](typeid-cpp-component-extensions.md)|

## <a name="declarators"></a>宣告子

下列類型宣告子會指示執行階段自動管理配置物件的存留期和刪除。

|運算子|用途|參考資料|
|--------------|-------------|---------------|
|`^`|宣告物件的控制代碼；也就是，一個指向 Windows 執行階段或 CLR 物件的指標，不再使用它時即會自動刪除。|[物件控制代碼運算子 (^)](handle-to-object-operator-hat-cpp-component-extensions.md)|
|`%`|宣告追蹤參考；也就是，Windows 執行階段或 CLR 物件的參考，不再使用它時即會自動刪除。|[追蹤參考運算子](tracking-reference-operator-cpp-component-extensions.md)|

## <a name="additional-constructs-and-related-topics"></a>其他建構和相關主題

本節列出與 CLR 有關的其他程式設計建構和主題。

|主題|說明|
|-----------|-----------------|
|[__identifier (C++/CLI)](identifier-cpp-cli.md)|(Windows 執行階段和 CLR) 可將關鍵字當作識別碼使用。|
|[變數引數清單 (...) (C++/CLI)](variable-argument-lists-dot-dot-dot-cpp-cli.md)|(Windows 執行階段和 CLR) 讓函式能夠接受可變數目的引數。|
|[C++ 原生類型的 .NET Framework 對等項 (C++/CLI)](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md)|列出用來取代 C++ 整數類型的 CLR 類型。|
|[appdomain](../cpp/appdomain.md) **__declspec** 修飾詞|**__declspec** 修飾詞，要求每個 appdomain 都有靜態和全域變數。|
|[使用 /clr 進行 C-Style 轉換 (C++/CLI)](c-style-casts-with-clr-cpp-cli.md)|描述 C-style 轉換的解譯方式。|
|[__clrcall](../cpp/clrcall.md) 呼叫慣例|表示 CLR 相容的呼叫慣例。|
|`__cplusplus_cli`|[預先定義的巨集](../preprocessor/predefined-macros.md)|
|[自訂屬性](user-defined-attributes-cpp-component-extensions.md)|描述如何定義您自己的 CLR 屬性。|
|[例外狀況處理](exception-handling-cpp-component-extensions.md)|提供例外狀況處理的概觀。|
|[明確覆寫](explicit-overrides-cpp-component-extensions.md)|示範成員函式如何覆寫任意成員。|
|[Friend 組件 (C++)](../dotnet/friend-assemblies-cpp.md)|討論用戶端組件如何存取組件元件中的所有類型。|
|[Boxing](boxing-cpp-component-extensions.md)|示範 boxed 處理值類型的條件。|
|[類型特徵的編譯器支援](compiler-support-for-type-traits-cpp-component-extensions.md)|討論如何在編譯時偵測類型的特性。|
|[managed、unmanaged](../preprocessor/managed-unmanaged.md) pragmas|示範 Managed 和 Unmanaged 函式如何共存於相同的模組。|
|[process](../cpp/process.md) **__declspec** 修飾詞|**__declspec** 修飾詞，要求每個 process 都有靜態和全域變數。|
|[反映 (C++/CLI)](../dotnet/reflection-cpp-cli.md)|示範執行階段類型資訊的 CLR 版本。|
|[String](string-cpp-component-extensions.md)|討論字串常值到 <xref:System.String> 的編譯器轉換。|
|[類型轉送 (C++/CLI)](type-forwarding-cpp-cli.md)|在傳送組件中讓類型移動到另一個組件，讓用戶端程式碼不需要重新編譯。|
|[使用者定義屬性](user-defined-attributes-cpp-component-extensions.md)|示範使用者定義屬性。|
|[#using 指示詞](../preprocessor/hash-using-directive-cpp.md)|匯入外部組件。|
|[XML 文件](../build/reference/xml-documentation-visual-cpp.md)|使用 [/doc (處理文件註解) (C/C++)](../build/reference/doc-process-documentation-comments-c-cpp.md) 來說明 XML 型程式碼文件|

## <a name="see-also"></a>另請參閱

[以 C++/CLI 進行 .NET 程式設計 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br/>
[原生和 .NET 互通性](../dotnet/native-and-dotnet-interoperability.md)