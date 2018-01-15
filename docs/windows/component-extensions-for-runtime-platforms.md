---
title: "執行階段平台的元件擴充功能 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- what's new [C++], keywords
- what's new [C++], language features
- Visual C++, keywords
- keywords [C++]
- Managed Extensions for C++, replacement syntax
ms.assetid: 1e400ee6-3ac9-4910-a608-9d3d5993e423
caps.latest.revision: "77"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e32057e17614da98c78d877fe95180dd02500909
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="component-extensions-for-runtime-platforms"></a>執行階段平台的元件擴充功能
Visual C++ 提供語言擴充功能，協助您針對執行階段平台進行程式設計。 使用 C + + /CX 中，您可以程式設計通用 Windows 平台應用程式和元件，編譯成原生程式碼。 雖然您可以透過 Windows 執行階段 COM 介面，直接對程式設計的方式建立通用 Windows 平台應用程式使用 C + + /CX 中，您可以使用建構函式、 例外狀況和其他現代 c + + 程式設計語言。 若要啟用 c + + 程式設計.NET 平台上 managed 的執行環境中，您可以使用 C + + /CLI。  
  
 **兩個執行階段，一組擴充功能**  
  
 C + + /CX 是子集 C + + /CLI。 擴充功能的通用的 C + + /CX 和 C + + CLI，語意取決於您的目標 common language runtime (CLR) 或 Windows 執行階段。 若要編譯您的應用程式在 Windows 執行階段上執行，請指定**/ZW**編譯器選項。 若要編譯它在 CLR 上執行，請指定**/clr**編譯器選項。 當您使用 Visual Studio 以建立專案時，會自動設定這些參數。  
  
 如需如何在 c + + 中建立通用 Windows 平台應用程式的詳細資訊，請參閱[藍圖的 Windows 執行階段應用程式使用 c + +](http://msdn.microsoft.com/library/windows/apps/hh700360.aspx)。  
  
 C + + CLI 延伸 ISO/ANSI c + + 標準，並定義在 Ecma C + + CLI 標準。 如需詳細資訊，請參閱[.NET 程式設計使用 C + + /CLI （Visual c + +）](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)。  
  
## <a name="data-type-keywords"></a>資料類型關鍵字  
 語言擴充功能包含*彙總關鍵字*，這是由空白字元分隔的兩個語彙基元所組成的關鍵字。 當語彙基元分開使用時，可能有一個意義，當它們一起使用時，則有另一個意義。 例如，"ref" 這個字是一般的識別項，而 "class" 這個字是宣告原生類別的關鍵字。 但當結合這些字，以形成`ref class`，產生的彙總關鍵字會宣告實體，也就是*執行階段類別*。  
  
 擴充功能也包括*即時線上*關鍵字。 關鍵字會被視為視內容而有所區別，取決於包含它的陳述式類型，以及它在該陳述式中的位置。 例如，語彙基元 "property" 可以是識別碼，或者它可以宣告一種特殊的公用類別成員。  
  
 下表列出在 C++ 語言擴充功能中的關鍵字。  
  
|關鍵字|視內容而有所區別|用途|參考資料|  
|-------------|-----------------------|-------------|---------------|  
|`ref class`<br /><br /> `ref struct`|否|宣告類型。|[類別和結構](../windows/classes-and-structs-cpp-component-extensions.md)|  
|`value class`<br /><br /> `value struct`|否|宣告值類型。|[類別和結構](../windows/classes-and-structs-cpp-component-extensions.md)|  
|`interface class`<br /><br /> `interface struct`|否|宣告介面。|[介面類別](../windows/interface-class-cpp-component-extensions.md)|  
|`enum class`<br /><br /> `enum struct`|否|宣告列舉。|[列舉類別](../windows/enum-class-cpp-component-extensions.md)|  
|`property`|[是]|宣告屬性。|[屬性](../windows/property-cpp-component-extensions.md)|  
|`delegate`|[是]|宣告委派。|[delegate (C++ 元件延伸模組)](../windows/delegate-cpp-component-extensions.md)|  
|`event`|[是]|宣告事件。|[event](../windows/event-cpp-component-extensions.md)|  
  
## <a name="override-specifiers"></a>覆寫規範  
 您可以使用下列關鍵字限定衍生的覆寫行為。 雖然 `new` 關鍵字不是 C++ 的擴充功能，它列在這裡是因為可以用於其他內容中。 某些規範對於原生程式設計也有效。 如需詳細資訊，請參閱[如何： 在原生編譯中宣告 「 覆寫規範 (C + + /CLI)](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)。  
  
|關鍵字|視內容而有所區別|用途|參考資料|  
|-------------|-----------------------|-------------|---------------|  
|`abstract`|[是]|表示函式或類別為抽象。|[abstract](../windows/abstract-cpp-component-extensions.md)|  
|`new`|否|表示函式不是基底類別版本的覆寫。|[new （新位置 vtable 中）](../windows/new-new-slot-in-vtable-cpp-component-extensions.md)|  
|`override`|[是]|表示方法必須是基底類別版本的覆寫。|[override](../windows/override-cpp-component-extensions.md)|  
|`sealed`|[是]|避免將類別做為基底類別。|[sealed](../windows/sealed-cpp-component-extensions.md)|  
  
## <a name="keywords-for-generics"></a>泛型的關鍵字  
 下列關鍵字已加入以支援泛型類型。 如需詳細資訊，請參閱[泛型](../windows/generics-cpp-component-extensions.md)。  
  
|關鍵字|視內容而有所區別|用途|  
|-------------|-----------------------|-------------|  
|`generic`|否|宣告泛型類型。|  
|`where`|[是]|指定套用至泛型類型參數的條件約束。|  
  
## <a name="miscellaneous-keywords"></a>其他關鍵字  
 下列關鍵字已加入至 C++ 擴充功能。  
  
|關鍵字|視內容而有所區別|用途|參考資料|  
|-------------|-----------------------|-------------|---------------|  
|`finally`|[是]|表示預設例外狀況處理行為。|[例外狀況處理](../windows/exception-handling-cpp-component-extensions.md)|  
|`for each, in`|否|列舉集合的項目。|[for each, in](../dotnet/for-each-in.md)|  
|`gcnew`|否|在記憶體回收堆積上配置類型。 改用 `new` 和 `delete`。|[ref 新 gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md)|  
|`ref new`|[是]|配置 [Windows 執行階段類型。 改用 `new` 和 `delete`。|[ref 新 gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md)|  
|`initonly`|[是]|表示成員只能在宣告或靜態建構函式中初始化。|[initonly (C++/CLI)](../dotnet/initonly-cpp-cli.md)|  
|`literal`|[是]|建立常值變數。|[常值](../windows/literal-cpp-component-extensions.md)|  
|`nullptr`|否|指出控制代碼或指標未指向物件。|[nullptr](../windows/nullptr-cpp-component-extensions.md)|  
  
## <a name="template-constructs"></a>範本建構  
 下列語言建構會實作為範本，而不是關鍵字。 如果您指定**/ZW**編譯器選項，其定義位於`lang`命名空間。 如果您指定**/clr**編譯器選項，其定義位於`cli`命名空間。  
  
|關鍵字|用途|參考資料|  
|-------------|-------------|---------------|  
|`array`|宣告陣列。|[陣列](../windows/arrays-cpp-component-extensions.md)|  
|`interior_ptr`|(只有 CLR) 指向參考類型中的資料。|[interior_ptr (C++/CLI)](../windows/interior-ptr-cpp-cli.md)|  
|`pin_ptr`|(只有 CLR) 指向 CLR 參考類型以暫時隱藏記憶體回收系統。|[pin_ptr (C++/CLI)](../windows/pin-ptr-cpp-cli.md)|  
|`safe_cast`|決定並執行執行階段類型的最佳轉型方法。|[safe_cast](../windows/safe-cast-cpp-component-extensions.md)|  
|`typeid`|(只有 CLR) 擷取 <xref:System.Type?displayProperty=fullName> 物件，該物件描述指定類型或物件。|[typeid](../windows/typeid-cpp-component-extensions.md)|  
  
## <a name="declarators"></a>宣告子  
 下列類型宣告子會指示執行階段自動管理配置物件的存留期和刪除。  
  
|運算子|用途|參考資料|  
|--------------|-------------|---------------|  
|`^`|宣告的控制代碼的物件。也就是說，會自動刪除時不再使用舊的 Windows 執行階段或 CLR 物件的指標。|[物件控制代碼運算子 (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)|  
|`%`|宣告追蹤參考。也就是說，會自動刪除時不再使用舊的 Windows 執行階段或 CLR 物件的參考。|[追蹤參考運算子](../windows/tracking-reference-operator-cpp-component-extensions.md)|  
  
## <a name="additional-constructs-and-related-topics"></a>其他建構和相關主題  
 本節列出與 CLR 有關的其他程式設計建構和主題。  
  
|主題|描述|  
|-----------|-----------------|  
|[__identifier (C++/CLI)](../windows/identifier-cpp-cli.md)|（Windows 執行階段和 CLR）啟用使用的關鍵字當做識別項。|  
|[變數引數清單 (...) (C++/CLI)](../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md)|（Windows 執行階段和 CLR）可讓函式接受可變數目的引數。|  
|[C++ 原生類型的 .NET Framework 對等項 (C++/CLI)](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md)|列出用來取代 C++ 整數類型的 CLR 類型。|  
|[appdomain](../cpp/appdomain.md) `__declspec`修飾詞|`__declspec` 修飾詞，要求每個 appdomain 都有靜態和全域變數。|  
|[使用 /clr 進行 C-style 轉換 (C + + /CLI)](../windows/c-style-casts-with-clr-cpp-cli.md)|描述 C-style 轉換的解譯方式。|  
|[__clrcall](../cpp/clrcall.md)呼叫慣例|表示 CLR 相容的呼叫慣例。|  
|`__cplusplus_cli`|[預先定義的巨集](../preprocessor/predefined-macros.md)|  
|[自訂屬性](../windows/custom-attributes-cpp.md)|描述如何定義您自己的 CLR 屬性。|  
|[例外狀況處理](../windows/exception-handling-cpp-component-extensions.md)|提供例外狀況處理的概觀。|  
|[明確覆寫](../windows/explicit-overrides-cpp-component-extensions.md)|示範成員函式如何覆寫任意成員。|  
|[Friend 組件 (C++)](../dotnet/friend-assemblies-cpp.md)|討論用戶端組件如何存取組件元件中的所有類型。|  
|[Boxing](../windows/boxing-cpp-component-extensions.md)|示範 boxed 處理值類型的條件。|  
|[類型特性的編譯器支援](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)|討論如何在編譯時偵測類型的特性。|  
|[managed、 unmanaged](../preprocessor/managed-unmanaged.md) pragma|示範 Managed 和 Unmanaged 函式如何共存於相同的模組。|  
|[處理序](../cpp/process.md)`__declspec`修飾詞|`__declspec` 修飾詞，要求每個程序都有靜態和全域變數。|  
|[反映 (C++/CLI)](../dotnet/reflection-cpp-cli.md)|示範執行階段類型資訊的 CLR 版本。|  
|[String](../windows/string-cpp-component-extensions.md)|討論字串常值到 <xref:System.String> 的編譯器轉換。|  
|[類型轉送 (C++/CLI)](../windows/type-forwarding-cpp-cli.md)|在傳送組件中讓類型移動到另一個組件，讓用戶端程式碼不需要重新編譯。|  
|[使用者定義的屬性](../windows/user-defined-attributes-cpp-component-extensions.md)|示範使用者定義屬性。|  
|[#using 指示詞](../preprocessor/hash-using-directive-cpp.md)|匯入外部組件。|  
|[XML 文件](../ide/xml-documentation-visual-cpp.md)|說明以 XML 為基礎的程式碼文件使用[/doc （處理文件註解） （C/c + +）](../build/reference/doc-process-documentation-comments-c-cpp.md)|  
  
## <a name="see-also"></a>請參閱  
 [.NET 程式設計使用 C + + /CLI （Visual c + +）](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)   
 [原生和 .NET 互通性](../dotnet/native-and-dotnet-interoperability.md)