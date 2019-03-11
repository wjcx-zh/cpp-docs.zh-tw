---
title: 類型系統 (C++/CX)
ms.date: 02/03/2017
ms.assetid: b67bee8a-b526-4872-969e-ef22724e88fe
ms.openlocfilehash: fbc7a178621624e396c80509703ce1b5b4c19162
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57745950"
---
# <a name="type-system-ccx"></a>類型系統 (C++/CX)

使用 Windows 執行階段架構，您可以使用 C + + /CX、 Visual Basic、 Visual C# 和 JavaScript 來撰寫應用程式和元件，直接存取 Windows API，並與其他 Windows 執行階段應用程式和元件相互操作。 在 c + + 撰寫的通用 Windows 平台應用程式編譯為直接在 CPU 中執行的原生程式碼。 以 C# 或 Visual Basic 撰寫的通用 Windows 平台應用程式編譯成 Microsoft intermediate language (MSIL)，並在 common language runtime (CLR) 中執行。 在執行階段環境中，執行以 JavaScript 撰寫的通用 Windows 平台應用程式。 Windows 執行階段作業系統元件本身是以 c + + 撰寫，並以原生程式碼執行。 所有這些元件和通用 Windows 平台應用程式直接透過 Windows 執行階段應用程式二進位介面 (ABI) 進行通訊。

若要啟用 Windows 執行階段在現代 c + + 慣用語中支援，Microsoft 建立了 C + + /CX。 C + + /CX 提供內建的基底型別和實作的基本 Windows 執行階段類型，可讓 c + + 應用程式和元件跨 ABI 與使用其他語言所撰寫的應用程式進行通訊。 您可以使用任何 Windows 執行階段型別，，或建立類別、 結構、 介面和其他使用者定義的型別，可供其他通用 Windows 平台應用程式和元件。 通用 Windows 平台應用程式撰寫的 C + + /CX 也可以使用一般的 c + + 類別和結構，只要他們沒有公用存取範圍。

如需 C++/CX 語言投影和其運作方式的深入討論，請參閱部落格文章：

1. [C + + /CX 第 0 部分\[n\]:簡介](https://blogs.msdn.microsoft.com/vcblog/2012/08/29/ccx-part-0-of-n-an-introduction)

1. [C + + /CX 第 1 部分\[n\]:簡單的類別](https://blogs.msdn.microsoft.com/vcblog/2012/09/05/ccx-part-1-of-n-a-simple-class)

1. [C + + /CX 第 2 部分\[n\]:戴帽子的](https://blogs.msdn.microsoft.com/vcblog/2012/09/17/ccx-part-2-of-n-types-that-wear-hats)

1. [C + + /CX 第 3 部分\[n\]:在建構](https://blogs.msdn.microsoft.com/vcblog/2012/10/05/ccx-part-3-of-n-under-construction/)

1. [C + + /CX 第 4 部分\[n\]:靜態成員函式](https://blogs.msdn.microsoft.com/vcblog/2012/10/19/ccx-part-4-of-n-static-member-functions)

## <a name="windows-metadata-winmd-files"></a>Windows 中繼資料 (.winmd) 檔案

當您編譯以 c + + 撰寫的通用 Windows 平台應用程式時，編譯器會產生可執行檔，以原生機器碼，並也會產生個別的 Windows 中繼資料 (.winmd) 檔案，包含公用的 Windows 執行階段類型，描述這包括類別、 結構、 列舉、 介面、 參數化的介面和委派。 中繼資料的格式類似 .NET Framework 組件中使用的格式。  在 C++ 元件中，.winmd 檔案只包含中繼資料，可執行程式碼位於另一個檔案中。 這是隨附於 Windows 的 Windows 執行階段元件的情況。 WinMD 檔案名稱必須符合原始程式碼中的根命名空間或為根命名空間的首碼。 (對於 .NET Framework 語言，.winmd 檔案包含程式碼和中繼資料，如同 .NET Framework 組件一樣)。

.winmd 檔案的中繼資料代表程式碼的發行介面。 已發行的類型會顯示其他通用 Windows 平台無論何種語言撰寫這些其他應用程式。 因此，中繼資料或您已發佈的程式碼，只可以包含 Windows 執行階段型別系統所指定的類型。 C++ 特有的語言建構無法在中繼資料中發行，例如標準類別、陣列、樣板或 STL 容器，因為 JavaScript 或 C# 用戶端應用程式無法處理它們。

類型或方法是否出現在中繼資料中，取決於套用哪些存取範圍修飾詞。 必須在命名空間中宣告類型，且必須宣告為公用，類型才能為可見。 您的程式碼中，允許非公用 ref 類別做為內部協助程式類型，只是在中繼資料中不可見。 即使在公用 ref 類別中，所有成員也不一定都可見。 下表列出公用 ref 類別中的 c + + 存取規範與 Windows 執行階段中繼資料可見性之間的關聯性：

|||
|-|-|
|**在中繼資料中發行**|**未在中繼資料中發行**|
|public|private|
|protected|internal|
|public protected|private protected|

您可以使用 [ **物件瀏覽器** ] 來檢視 .winmd 檔案的內容。 隨附於 Windows 的 Windows 執行階段元件是 Windows.winmd 檔案中。 Default.winmd 檔案包含的基本類型，可在 C + + /CX 中和 platform.winmd 包含來自 Platform 命名空間的其他型別。 根據預設，會將這三個.winmd 檔案包含通用 Windows 平台應用程式之每個 c + + 專案中。

> [!TIP]
> 因為 [Platform::Collections Namespace](../cppcx/platform-collections-namespace.md) 中的類型不是公用的，所以不會出現在 .winmd 檔案中。 它們是 `Windows::Foundation::Collections`中定義的介面的私用 C++ 專屬實作。 以 JavaScript 或 C# 撰寫的 Windows 執行階段應用程式不知道[3&gt;platform::collections::map](../cppcx/platform-collections-vector-class.md) ，但可以使用`Windows::Foundation::Collections::IVector`。 `Platform::Collections` 類型在 collection.h 中定義。

## <a name="windows-runtime-type-system-in-ccx"></a>Windows 執行階段類型系統，在 C + + /CX

下列各節描述的主要功能的 Windows 執行階段類型系統，以及它們如何支援在 C + + /CX。

### <a name="namespaces"></a>命名空間

所有的 Windows 執行階段類型必須宣告在命名空間中;Windows API 本身被依命名空間。 .winmd 檔案必須具有根命名空間的相同名稱。 例如，名為 A.B.C.MyClass 的類別必須在名為 A.winmd、A.B.winmd 或 A.B.C.winmd 的中繼資料檔案中定義，才能執行個體化。 DLL 的名稱不需符合 .winmd 檔案名稱。

Windows API 本身已改造成一套以命名空間組織的構造良好類別庫。  在 windows.* 命名空間中宣告所有的 Windows 執行階段元件。

如需詳細資訊，請參閱 <<c0> [ 命名空間和類型可視性](../cppcx/namespaces-and-type-visibility-c-cx.md)。

### <a name="fundamental-types"></a>基本類型

Windows 執行階段定義下列基本型別、 UInt8、 Int16、 UInt16、 Int32、 UInt32、 Int64、 UInt64、 單一、 Double、 Char16、 布林值和字串。 C + + /CX 支援其預設命名空間中的基本數值類型，作為 uint16、 uint32、 uint64、 int16、 int32、 int64、 float32、 float64 和 char16。 Boolean 和 String 也在 Platform 命名空間中定義。

C + + /CX 也定義 uint8，相當於`unsigned char`，它不支援在 Windows 執行階段，並不能在公用 Api。

透過將基本型別包裝在 [Platform::IBox 介面](../cppcx/platform-ibox-interface.md) 中，它就能成為可為 Null 的型別。 如需詳細資訊，請參閱 [實值類別與結構](../cppcx/value-classes-and-structs-c-cx.md)中定義的介面的私用 C++ 專屬實作。

如需基本型別的詳細資訊，請參閱 [基本類型](../cppcx/fundamental-types-c-cx.md)

### <a name="strings"></a>字串

Windows 執行階段字串是 16 位元 UNICODE 字元的不可變的序列。 Windows 執行階段字串`Platform::String^`。 這個類別提供建構、操作及與 `wchar_t`之間轉換字串的方法。

如需詳細資訊，請參閱 [字串](../cppcx/strings-c-cx.md)中定義的介面的私用 C++ 專屬實作。

### <a name="arrays"></a>陣列

Windows 執行階段支援任何型別的 1 維陣列。 不支援巢狀陣列。  在 C + + /CX 中，Windows 執行階段陣列以[platform:: array 類別](../cppcx/platform-array-class.md)。

如需詳細資訊，請參閱[Array 和 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)

### <a name="ref-classes-and-structs"></a>Ref 類別與結構

Windows 執行階段類別預計在 C + + /CX 為 ref 類別或 ref 結構表示，因為它們傳址方式複製。 ref 類別和 ref 結構的記憶體管理是由參考計數自動處理。 當物件的最後一個參考超出範圍時，就會終結物件。 ref 類別或 ref 結構可以：

- 包含成員建構函式、方法、屬性和事件。 這些成員可以有 public、private、protected 或 internal 存取範圍。

- 可以包含私用巢狀列舉、結構或類別定義。

- 可以直接繼承自一個基底類別，也可以實作任意數目的介面。 所有 ref 類別都會隱含轉換為 [Platform::Object Class](../cppcx/platform-object-class.md) ，而且也都能覆寫其虛擬方法 (例如 [Object::ToString](../cppcx/platform-object-class.md#tostring))。

具有公用建構函式的 ref 類別必須宣告為密封，以避免進一步衍生。

如需詳細資訊，請參閱 [Ref 類別與結構](../cppcx/ref-classes-and-structs-c-cx.md)

### <a name="value-classes-and-structs"></a>實值類別與結構

實值類別或實值結構代表基本資料結構，且只包含欄位，可能是實值類別、實值結構或型別 `Platform::String^`。  實值結構和實值類別是以傳值方式複製。

透過將實值結構包裝在 IBox 介面中，它就能成為可為 Null 的結構。

如需詳細資訊，請參閱 [實值類別與結構](../cppcx/value-classes-and-structs-c-cx.md)中定義的介面的私用 C++ 專屬實作。

### <a name="partial-classes"></a>部分類別

部分類別功能可讓您在多個檔案中定義一個類別。 它主要是用來讓程式碼產生工具 (例如 XAML 編輯器) 可以修改某個檔案，而不會修改到您編輯的檔案。

如需詳細資訊，請參閱 [部分類別](../cppcx/partial-classes-c-cx.md)

### <a name="properties"></a>屬性

屬性的任何 Windows 執行階段類型的公用資料成員，且會實作為 get/set 方法組。 用戶端程式碼將屬性視為公用欄位來存取。 不需要自訂 get 或 set 程式碼的屬性稱為 *trivial 屬性* ，可宣告為不具有明確的 get 或 set 方法。

如需詳細資訊，請參閱 [屬性](../cppcx/properties-c-cx.md)。

### <a name="windows-runtime-collections-in-ccx"></a>Windows 執行階段集合，在 C + + /CX

Windows 執行階段會定義一組之集合型別的各種語言以自己的方式實作的介面。 C + + /CX 提供中的實作[3&gt;platform::collections::map](../cppcx/platform-collections-vector-class.md)， [std:: map 類別](../cppcx/platform-collections-map-class.md)，及其他相關的具象集合類型，也就是相容於其標準範本庫 (STL) 對應項目。

如需詳細資訊，請參閱 <<c0> [ 集合](../cppcx/collections-c-cx.md)。

### <a name="template-ref-classes"></a>樣板 ref 類別

您可以為私用和內部 ref 類別建立樣板並加以特製化。

如需詳細資訊，請參閱 [樣板 ref 類別](../cppcx/template-ref-classes-c-cx.md)中定義的介面的私用 C++ 專屬實作。

### <a name="interfaces"></a>介面

Windows 執行階段介面會定義一組公用屬性、 方法和 ref 類別或 ref 結構都必須實作它所繼承之介面的事件。

如需詳細資訊，請參閱[介面](../cppcx/interfaces-c-cx.md)。

### <a name="enums"></a>列舉

Windows 執行階段中的列舉類別類似於 c + + 中的範圍的列舉。 基礎類型是 int32，但如果套用 [Flags] 屬性，則基礎類型是 uint32。

如需詳細資訊，請參閱 [列舉](../cppcx/enums-c-cx.md)中定義的介面的私用 C++ 專屬實作。

### <a name="delegates"></a>委派

在 Windows 執行階段委派是類似於 c + + 中的 std:: function 物件。 這是特殊類型的 ref 類別，用來叫用用戶端提供的函式 (具有相容簽章)。  Windows 執行階段中最常使用委派做為事件的類型。

如需詳細資訊，請參閱[委派](../cppcx/delegates-c-cx.md)。

### <a name="exceptions"></a>例外狀況

在 C++/CX 中，您可以攔截自訂例外狀況類型、 [std::exception](../standard-library/exception-class.md) 類型和 [Platform::Exception](../cppcx/platform-exception-class.md) 類型。

如需詳細資訊，請參閱 [例外狀況](../cppcx/exceptions-c-cx.md)中定義的介面的私用 C++ 專屬實作。

### <a name="events"></a>事件

事件是 ref 類別或 ref 結構中具有委派型別的公用成員。 事件只能由主控類別叫用，也就是引發。 不過，用戶端程式碼可以提供自己的函式，也稱為事件處理常式，在主控類別引發事件時叫用。

如需詳細資訊，請參閱 [事件](../cppcx/events-c-cx.md)中定義的介面的私用 C++ 專屬實作。

### <a name="casting"></a>轉型

C++/CX 支援標準 C++ 轉型運算子 [static_cast](../cpp/static-cast-operator.md)、 [dynamic_cast](../cpp/dynamic-cast-operator.md)和 [reinterpret_cast](../cpp/reinterpret-cast-operator.md)。此外， **safe_cast** 也是 C++/CX 專用的運算子。

如需詳細資訊，請參閱 [轉型](../cppcx/casting-c-cx.md)中定義的介面的私用 C++ 專屬實作。

### <a name="boxing"></a>Boxing

Boxed 變數是在必須有參考語意的情況下，包裝在參考類型中的實值類型。

如需詳細資訊，請參閱 [Boxing](../cppcx/boxing-c-cx.md)中定義的介面的私用 C++ 專屬實作。

### <a name="attributes"></a>屬性

屬性是中繼資料值可以套用至任何 Windows 執行階段類型或類型成員，而且可以在執行階段檢查。 Windows 執行階段定義的通用屬性中的一組`Windows::Foundation::Metadata`命名空間。 Windows 執行階段在此版本中不支援公用介面上的使用者定義的屬性。

## <a name="api-deprecation"></a>API 取代

描述如何將公用 Api 標記為使用相同的屬性，可由 Windows 執行階段系統型別已被取代。

如需詳細資訊，請參閱 <<c0> [ 即將淘汰的類型和成員](../cppcx/deprecating-types-and-members-c-cx.md)。

## <a name="see-also"></a>另請參閱

[Visual c + + 語言參考](../cppcx/visual-c-language-reference-c-cx.md)
