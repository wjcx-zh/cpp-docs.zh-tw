---
title: "轉型 (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5247f6c7-6a0a-4021-97c9-21c868bd9455
caps.latest.revision: 15
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 15
---
# 轉型 (C++/CX)
[!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]類型可以使用四種不同的轉換運算子：[static\_cast 運算子](../cpp/static-cast-operator.md)、[dynamic\_cast 運算子](../cpp/dynamic-cast-operator.md)、[safe\_cast 運算子](~/windows/safe-cast-cpp-component-extensions.md)和 [reinterpret\_cast 運算子](../cpp/reinterpret-cast-operator.md)。 如果無法執行轉換，`safe_cast` 和 `static_cast` 會擲回例外狀況。此外，[static\_cast 運算子](../cpp/static-cast-operator.md)也可以執行編譯階段類型檢查。 如果 `dynamic_cast` 無法轉換類型，則會傳回 `nullptr`。 雖然 `reinterpret_cast` 會傳回非 null 值，但是可能無效。 因此，我們建議您不要使用 `reinterpret_cast`，除非您知道轉型成功。 此外，我們也建議您不要在 [!INCLUDE[cppwrt](../cppcx/includes/cppwrt-md.md)] \([!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]\) 程式碼中使用 C\-style 轉型，因為它們與 `reinterpret_cast` 相同。  
  
 編譯器和執行階段也會執行隱含轉型，例如，當實值類型或內建類型當做引數傳遞給參數類型為 `Object^` 的方法時，所進行的 boxing 作業。 理論上，隱含轉型不應該在執行階段造成例外狀況。如果編譯器無法執行隱含轉換，則會在編譯時期引發錯誤。  
  
 [!INCLUDE[cppwrt](../cppcx/includes/cppwrt-md.md)]是 COM 的抽象概念，它會使用 HRESULT 錯誤碼而不是例外狀況。 一般而言，[Platform::InvalidCastException](../cppcx/platform-invalidcastexception-class.md) 表示 E\_NOINTERFACE 的低階 COM 錯誤。  
  
## static\_cast  
 編譯時期會檢查 `static_cast`，以判斷兩個類型之間是否有繼承關係。 如果這兩個類型不相關，則轉型會造成編譯器錯誤。  
  
 在 ref 類別上執行 `static_cast`，會導致執行階段檢查。 ref 類別中的 `static_cast` 雖然通過編譯時期驗證，但是仍然可能會在執行階段失敗，在此情況下會擲回 `Platform::InvalidCastException`。 一般而言，您不必處理這些例外狀況，因為這些例外狀況幾乎都表示可在開發和測試階段排除的程式設計錯誤。  
  
 如果程式碼明確宣告兩個類型之間的關聯性，因此您確定轉型應該會成功，請使用 `static_cast`。  
  
```  
interface class A{}; public ref class Class1 sealed : A { }; ... A^ obj = ref new Class1(); // Class1 is an A // You know obj is a Class1. The compiler verifies that this is possible, and in C++/CX a run-time check is also performed. Class1^ c = static_cast<Class1^>(obj);  
  
```  
  
## safe\_cast  
 `safe_cast` 運算子是 [!INCLUDE[cppwrt](../cppcx/includes/cppwrt-md.md)]的一部分。 它會執行執行階段類型檢查，並在轉換失敗時擲回 `Platform::InvalidCastException`。 當執行階段失敗表示例外狀況時，請使用 `safe_cast`。`safe_cast` 的主要目的是為了在其發生的開發和測試階段協助識別程式設計錯誤。 您不必處理此例外狀況，因為未處理的例外狀況本身會識別失敗點。  
  
 如果程式碼未宣告關聯性，但是您確定轉型應該會成功，請使用 safe\_cast。  
  
```  
  
// A and B are not related interface class A{}; interface class B{}; public ref class Class1 sealed : A, B { }; ... A^ obj = ref new Class1(); // You know that obj’s backing type implements A and B, but // the compiler can’t tell this by comparing A and B. The run-time type check succeeds. B^ obj2 = safe_cast<B^>(obj);  
  
```  
  
## dynamic\_cast  
 當您將物件 \(更明確地說，也就是 hat ‘^’\) 轉換成衍生程度較大的類型時，請使用 `dynamic_cast`，您會預期目標物件有時可能會是 `nullptr` 或轉型可能會失敗，而且您會想要將這個情況當做正常程式碼路徑來處理，而不是當做例外狀況。 例如，在 \[**Windows 市集空白應用程式**\] 專案範本中，`OnLaunched` 中的 `app.xamp.cpp` 方法會使用 `dynamic_cast` 測試應用程式視窗是否有內容。 如果它沒有內容也並非錯誤，因為這是預期的情況。`Windows::Current::Content` 是 `Windows::UI::XAML::UIElement` 並且會轉換為 `Windows::UI.XAML::Controls::Frame`，這在繼承階層架構中是屬於衍生程度較高的類型。  
  
```  
void App::OnLaunched(Windows::ApplicationModel::Activation::LaunchActivatedEventArgs^ args) { auto rootFrame = dynamic_cast<Frame^>(Window::Current->Content); // Do not repeat app initialization when the window already has content, // just ensure that the window is active if (rootFrame == nullptr) { // Create a Frame to act as the navigation context and associate it with // a SuspensionManager key rootFrame = ref new Frame(); ...  
```  
  
 `dynamic_cast` 的另一個用途是探查 `Object^` 來判斷它是否包含 Boxed 實值類型。 在這種情況下，您會嘗試 `dynamic_cast<Platform::Box>` 或 `dynamic_cast<Platform::IBox>`。  
  
 **dynamic\_cast 和追蹤參考 \(%\)**  
  
 您也可以將 `dynamic_cast` 套用至追蹤參考，不過在此情況下，轉型的行為類似於 `safe_cast`。 它會在失敗時擲回 `Platform::InvalidCastException`，因為追蹤參考不能有 `nullptr` 值。  
  
## reinterpret\_cast  
 我們建議您不要使用 [reinterpret\_cast](../cpp/reinterpret-cast-operator.md)，因為編譯時期檢查和執行階段檢查都不會執行。 在最糟的狀況下，`reinterpret_cast` 會讓程式設計錯誤無法在開發階段被偵測到，而且可能會對程式的行為造成微妙或災難性的錯誤。 因此，我們建議您只有在必須於不相關的類型之間轉型，而且您知道轉型將會成功的罕見情況下，才能使用 `reinterpret_cast`。 罕見用途的範例如下：將 [!INCLUDE[cppwrt](../cppcx/includes/cppwrt-md.md)] 型别轉換成其基礎 ABI 類型，這表示您會控制此物件的參考計數。 若要這麼做，我們建議您使用 [ComPtr 類別](../windows/comptr-class.md)智慧型指標。 否則，您必須在介面上特別呼叫 Release。 下列範例示範如何將 ref 類別轉型為 `IInspectable*`。  
  
```  
  
#include <wrl.h> using namespace Microsoft::WRL; auto winRtObject = ref new SomeWinRTType(); ComPtr<IInspectable> inspectable = reinterpret_cast<IInspectable*>(obj2); ...  
  
```  
  
 如果您使用 `reinterpret_cast` 從某個 [!INCLUDE[cppwrt](../cppcx/includes/cppwrt-md.md)]介面轉換為另一個介面，將會導致此物件釋出兩次。 因此，只有當您轉換成非 [!INCLUDE[cppwrt](../cppcx/includes/cppwrt-md.md)]介面時，才能使用這個轉型。  
  
 **ABI 類型**  
  
-   ABI 類型存在於 Windows SDK 的標頭中。 為了方便起見，標頭會以命名空間命名，例如 `windows.storage.h`。  
  
-   ABI 類型存在於特殊命名空間 ABI 中，例如 `ABI::Windows::Storage::Streams::IBuffer*`。  
  
-   在 [!INCLUDE[cppwrt](../cppcx/includes/cppwrt-md.md)]介面類型與其對等 ABI 類型之間轉換永遠是安全的，也就是從 `IBuffer^` 轉換為 `ABI::IBuffer*`。  
  
-   [!INCLUDE[cppwrt](../cppcx/includes/cppwrt-md.md)]執行階段類別永遠都應該轉換為 `IInspectable*` 或其預設介面 \(如果預設介面已知的話\)。  
  
-   在轉換成 ABI 類型之後，您會擁有此類型的存留期，而且必須遵循 COM 規則。 我們建議您使用 `WRL::ComPtr` 來簡化 ABI 指標的存留期管理。  
  
 下表摘要說明可安全使用 `reinterpret_cast` 的案例。 在每個案例中，雙向轉型是安全的。  
  
|||  
|-|-|  
|HSTRING|String^|  
|HSTRING\*|String^\*|  
|IInspectable\*|Object^|  
|IInspectable\*\*|Object^\*|  
|IInspectable\-derived\-type\*|same\-interface\-from\-winmd^|  
|IInspectable\-derived\-type\*\*|same\-interface\-from\-winmd^\*|  
|IDefault\-interface\-of\-RuntimeClass\*|same\-RefClass\-from\-winmd^|  
|IDefault\-interface\-of\-RuntimeClass\*\*|same\-RefClass\-from\-winmd^\*|  
  
## 請參閱  
 [類型系統](../cppcx/type-system-c-cx.md)   
 [Visual C\+\+ 語言參考](../cppcx/visual-c-language-reference-c-cx.md)   
 [命名空間參考](../cppcx/namespaces-reference-c-cx.md)