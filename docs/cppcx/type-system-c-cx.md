---
title: "類型系統 (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "02/03/2017"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b67bee8a-b526-4872-969e-ef22724e88fe
caps.latest.revision: 28
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 28
---
# 類型系統 (C++/CX)
[!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]架構可讓您使用 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]、Visual Basic、Visual C\# 和 JavaScript 來撰寫應用程式和元件，以直接存取 Windows API 並與其他 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]應用程式和元件相互操作。 以 C\+\+ 撰寫的 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]應用程式會編譯為直接在 CPU 中執行的機器碼。 以 C\# 或 Visual Basic 撰寫的 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]應用程式會編譯成 Microsoft Intermediate Language \(MSIL\)，並在 Common Language Runtime \(CLR\) 中執行。 以 JavaScript 撰寫的 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]應用程式在執行階段環境中執行。[!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]作業系統元件本身以 C\+\+ 撰寫，且以機器碼形式執行。 這些元件和 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]應用程式全部都透過 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]應用程式二進位介面 \(ABI\) 直接通訊。  
  
 為了在現代 C\+\+ 慣用語中支援 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]，Microsoft 建立 [!INCLUDE[cppwrt](../cppcx/includes/cppwrt-md.md)] \([!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]\)。[!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 提供基本 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]類型的內建基底類型和實作，可讓 C\+\+ 應用程式和元件透過 ABI，而與以其他語言撰寫的應用程式通訊。 您可以使用任何 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]類型，或建立可供其他 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]應用程式和元件使用的類別、結構、介面及其他使用者定義類型。 以 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)] 撰寫的 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]應用程式，也可以使用沒有公用存取範圍的標準 C\+\+ 類別和結構。  
  
 如需 C\+\+\/CX 語言投影和其運作方式的深入討論，請參閱部落格文章：  
  
1.  [C\+\+\/CX \[n\] 的第 0 部分：簡介](http://blogs.msdn.com/b/vcblog/archive/2012/08/29/cxxcxpart00anintroduction.aspx)  
  
2.  [C\+\+\/CX \[n\] 的第 0 部分：簡介](http://blogs.msdn.com/b/vcblog/archive/2012/08/29/cxxcxpart00anintroduction.aspx)  
  
3.  [C\+\+\/CX \[n\] 的第 2 部分：戴帽子的類別](http://blogs.msdn.com/b/vcblog/archive/2012/09/17/cxxcxpart02typesthatwearhats.aspx)  
  
4.  [C\+\+\/CX \[n\] 的第 3 部分：建構中](http://blogs.msdn.com/b/vcblog/archive/2012/10/05/cxxcxpart03underconstruction.aspx)  
  
5.  [C\+\+\/CX \[n\] 的第 4 部分：靜態成員函式](http://blogs.msdn.com/b/vcblog/archive/2012/10/19/cxxcxpart04staticmemberfunctions.aspx)  
  
## Windows 中繼資料 \(.winmd\) 檔案  
 在編譯以 C\+\+撰寫的 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]應用程式時，編譯器會以原生機器碼產生可執行檔，也會產生包含公用 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]類型描述的個別 Windows 中繼資料 \(.winmd\) 檔案，這些類型包括類別、結構、列舉，介面、參數化介面及委派。 中繼資料的格式類似 .NET Framework 組件中使用的格式。  在 C\+\+ 元件中，.winmd 檔案只包含中繼資料，可執行程式碼位於另一個檔案中。 Windows 隨附的 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]元件就是這樣。 WinMD 檔案名稱必須符合原始程式碼中的根命名空間或為根命名空間的首碼。 \(對於 .NET Framework 語言，.winmd 檔案包含程式碼和中繼資料，如同 .NET Framework 組件一樣\)。  
  
 .winmd 檔案的中繼資料代表程式碼的發行介面。 其他 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]可看見發行類型，而不論這些應用程式以何種語言撰寫。 因此，中繼資料或發行程式碼只能包含 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]類型系統所指定的類型。 C\+\+ 特有的語言建構無法在中繼資料中發行，例如標準類別、陣列、樣板或 STL 容器，因為 JavaScript 或 C\# 用戶端應用程式無法處理它們。  
  
 類型或方法是否出現在中繼資料中，取決於套用哪些存取範圍修飾詞。 必須在命名空間中宣告類型，且必須宣告為公用，類型才能為可見。 您的程式碼中，允許非公用 ref 類別做為內部協助程式類型，只是在中繼資料中不可見。 即使在公用 ref 類別中，所有成員也不一定都可見。 下表列出公用 ref 類別中的 C\+\+ 存取規範與 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]中繼資料可見度之間的關聯性：  
  
|||  
|-|-|  
|**在中繼資料中發行**|**未在中繼資料中發行**|  
|public|private|  
|protected|internal|  
|public protected|private protected|  
  
 您可以使用 \[**物件瀏覽器**\] 來檢視 .winmd 檔案的內容。 Windows 隨附的 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]元件在 Windows.winmd 檔案中。 default.winmd 檔案包含 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 中使用的基本類型，platform.winmd 包含來自 Platform 命名空間的其他類型。 根據預設，[!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]應用程式的每個 C\+\+ 專案都包含這三個 .winmd 檔案。  
  
> [!TIP]
>  因為 [Platform::Collections 命名空間](../cppcx/platform-collections-namespace.md) 中的類型不是公用的，所以不會出現在 .winmd 檔案中。 它們是 `Windows::Foundation::Collections` 中定義的介面的私用 C\+\+ 專屬實作。 以 JavaScript 或 C\# 撰寫的 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]應用程式無法辨識 [Platform::Collections::Vector 類別](../cppcx/platform-collections-vector-class.md)，但可以使用 `Windows::Foundation::Collections::IVector`。`Platform::Collections` 類型在 collection.h 中定義。  
  
## [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 中的 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]類型系統  
 下列章節描述 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]類型系統的主要功能，以及 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 中如何支援這些功能。  
  
### 命名空間  
 所有 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]類型必須在命名空間內宣告，而 Windows API 本身以命名空間來組織。 .winmd 檔案必須具有根命名空間的相同名稱。 例如，名為 A.B.C.MyClass 的類別必須在名為 A.winmd、A.B.winmd 或 A.B.C.winmd 的中繼資料檔案中定義，才能執行個體化。 DLL 的名稱不需符合 .winmd 檔案名稱。  
  
 Windows API 本身已改造成一套以命名空間組織的構造良好類別庫。  所有 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]元件在 Windows.\* 命名空間中宣告。  
  
 如需詳細資訊，請參閱[命名空間和類型可視性](../cppcx/namespaces-and-type-visibility-c-cx.md)。  
  
### 基本類型  
 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]定義下列基本類型：UInt8、Int16、UInt16、Int32、UInt32、Int64、UInt64、Single、Double、Char16、Boolean 和 String。[!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 支援預設命名空間中的基本數值類型，包括 uint16、uint32、uint64、int16、int32、int64、float32、float64 和 char16。 Boolean 和 String 也在 Platform 命名空間中定義。  
  
 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 也定義 uint8，相當於 `unsigned char`，此型別在 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]中不受支援，也不能在公用 API 中使用。  
  
 透過將基本型別包裝在 [Platform::IBox 介面](../cppcx/platform-ibox-interface.md)中，它就能成為可為 Null 的型別。 如需詳細資訊，請參閱[實值類別與結構](../cppcx/value-classes-and-structs-c-cx.md)。  
  
 如需基本型別的詳細資訊，請參閱[基本類型](../cppcx/fundamental-types-c-cx.md)。  
  
### 字串  
 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]字串是不可變的 16 位元 UNICODE 字元序列。[!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]字串以 `Platform::String^` 表示。 這個類別提供建構、操作及與 `wchar_t` 之間轉換字串的方法。  
  
 如需詳細資訊，請參閱[字串](../cppcx/strings-c-cx.md)。  
  
### 陣列  
 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]支援任何型別的 1 維陣列 不支援巢狀陣列。  在 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 中，[!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]陣列以 [Platform::Array 類別](../cppcx/platform-array-class.md) 表示。  
  
 如需詳細資訊，請參閱[Array 和 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)。  
  
### Ref 類別與結構  
 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]類別在 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 中以 ref 類別或 ref 結構表示，因為它們是以傳址方式複製。 ref 類別和 ref 結構的記憶體管理是由參考計數自動處理。 當物件的最後一個參考超出範圍時，就會終結物件。 ref 類別或 ref 結構可以：  
  
-   包含成員建構函式、方法、屬性和事件。 這些成員可以有 public、private、protected 或 internal 存取範圍。  
  
-   可以包含私用巢狀列舉、結構或類別定義。  
  
-   可以直接繼承自一個基底類別，也可以實作任意數目的介面。 所有 ref 類別都會隱含轉換為 [Platform::Object 類別](../cppcx/platform-object-class.md)，而且也都能覆寫其虛擬方法 \(例如 [Object::ToString](../cppcx/object-tostring-method-c-cx.md)\)。  
  
 具有公用建構函式的 ref 類別必須宣告為密封，以避免進一步衍生。  
  
 如需詳細資訊，請參閱[Ref 類別與結構](../cppcx/ref-classes-and-structs-c-cx.md)。  
  
### 實值類別與結構  
 實值類別或實值結構代表基本資料結構，且只包含欄位，可能是實值類別、實值結構或型別 `Platform::String^`。  實值結構和實值類別是以傳值方式複製。  
  
 透過將實值結構包裝在 IBox 介面中，它就能成為可為 Null 的結構。  
  
 如需詳細資訊，請參閱[實值類別與結構](../cppcx/value-classes-and-structs-c-cx.md)。  
  
### 部分類別  
 部分類別功能可讓您在多個檔案中定義一個類別。 它主要是用來讓程式碼產生工具 \(例如 XAML 編輯器\) 可以修改某個檔案，而不會修改到您編輯的檔案。  
  
 如需詳細資訊，請參閱[部分類別](../cppcx/partial-classes-c-cx.md)。  
  
### 屬性  
 屬性是任何 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]型別的公用資料成員，實作為一對 get\/set 方法。 用戶端程式碼將屬性視為公用欄位來存取。 不需要自訂 get 或 set 程式碼的屬性稱為 *trivial 屬性*，可宣告為不具有明確的 get 或 set 方法。  
  
 如需詳細資訊，請參閱[屬性](../cppcx/properties-c-cx.md)。  
  
### [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 中的 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]集合  
 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]定義集合類型的一組介面，由各種語言以自己的方式實作。[!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 在 [Platform::Collections::Vector 類別](../cppcx/platform-collections-vector-class.md)、 [Platform::Collections::Map 類別](../cppcx/platform-collections-map-class.md)和其他相關的具象集合類型中提供實作，與其 Standard Template Library \(STL\) 對應項目相容。  
  
 如需詳細資訊，請參閱[集合](../cppcx/collections-c-cx.md)。  
  
### 樣板 ref 類別  
 您可以為私用和內部 ref 類別建立樣板並加以特製化。  
  
 如需詳細資訊，請參閱[範本 ref 類別](../cppcx/template-ref-classes-c-cx.md)。  
  
### 介面  
 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]介面定義一組公用屬性、方法和事件，繼承自此介面的 ref 類別或 ref 結構都必須實作。  
  
 如需詳細資訊，請參閱[介面](../cppcx/interfaces-c-cx.md)。  
  
### 列舉  
 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]中的列舉類別類似於 C\+\+ 中的限定範圍列舉。 基礎類型是 int32，但如果套用 \[Flags\] 屬性，則基礎類型是 uint32。  
  
 如需詳細資訊，請參閱[列舉](../cppcx/enums-c-cx.md)。  
  
### 委派  
 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]的委派類似於 C\+\+ 中的 std::function 物件。 這是特殊類型的 ref 類別，用來叫用用戶端提供的函式 \(具有相容簽章\)。[!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]中最常以委派作為事件的類型。  
  
 如需詳細資訊，請參閱[委派](../cppcx/delegates-c-cx.md)。  
  
### 例外狀況  
 在 C\+\+\/CX 中，您可以攔截自訂例外狀況類型、[std::exception](../Topic/exception%20Class1.md) 類型和 [Platform::Exception](../cppcx/platform-exception-class.md) 類型。  
  
 如需詳細資訊，請參閱[例外狀況](../cppcx/exceptions-c-cx.md)。  
  
### 事件  
 事件是 ref 類別或 ref 結構中具有委派型別的公用成員。 事件只能由主控類別叫用，也就是引發。 不過，用戶端程式碼可以提供自己的函式，也稱為事件處理常式，在主控類別引發事件時叫用。  
  
 如需詳細資訊，請參閱[事件](../cppcx/events-c-cx.md)。  
  
### 轉型  
 C\+\+\/CX 支援標準 C\+\+ 轉型運算子 [static\_cast](../cpp/static-cast-operator.md)、[dynamic\_cast](../cpp/dynamic-cast-operator.md) 和 [reinterpret\_cast](../cpp/reinterpret-cast-operator.md)。此外，[safe\_cast](../Topic/safe_cast%20\(C++%20Component%20Extensions\).md) 也是 C\+\+\/CX 專用的運算子。  
  
 如需詳細資訊，請參閱[轉型](../cppcx/casting-c-cx.md)。  
  
### Boxing  
 Boxed 變數是在必須有參考語意的情況下，包裝在參考類型中的實值類型。  
  
 如需詳細資訊，請參閱[Boxing](../cppcx/boxing-c-cx.md)。  
  
### 屬性  
 屬性是可套用至任何 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]型別或型別成員的中繼資料值，可在執行階段檢查。[!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]在 `Windows::Foundation::Metadata` 命名空間中定義一組通用屬性。 這個版本的 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]不支援公用介面上的使用者定義屬性。  
  
## API 取代  
 描述如何使用 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]系統類型所用的相同屬性，將公用 API 標記為已被取代。  
  
 如需詳細資訊，請參閱[將類型和成員設為已被取代](../cppcx/deprecating-types-and-members-c-cx.md)。  
  
## 請參閱  
 [Visual C\+\+ 語言參考](../cppcx/visual-c-language-reference-c-cx.md)