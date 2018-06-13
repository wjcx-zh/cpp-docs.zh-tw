---
title: 轉型 (C + + /CX) |Microsoft 文件
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 5247f6c7-6a0a-4021-97c9-21c868bd9455
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8f71be537ecc0dc0cb58a3ada13612dbe8cbd7d3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33090953"
---
# <a name="casting-ccx"></a>轉型 (C++/CX)
適用於 Windows 執行階段類型的四個不同的轉換運算子： [static_cast 運算子](../cpp/static-cast-operator.md)， [dynamic_cast 運算子](../cpp/dynamic-cast-operator.md)， **safe_cast 運算子**，和[reinterpret_cast 運算子](../cpp/reinterpret-cast-operator.md)。 如果無法執行轉換，`safe_cast` 和 `static_cast` 會擲回例外狀況。此外， [static_cast 運算子](../cpp/static-cast-operator.md) 也可以執行編譯階段類型檢查。 如果`dynamic_cast` 無法轉換類型，則會傳回 `nullptr` 。 雖然 `reinterpret_cast` 會傳回非 null 值，但是可能無效。 因此，我們建議您不要使用 `reinterpret_cast` ，除非您知道轉型成功。 此外，我們建議您不要使用 c-style 轉型您 C + /CX 程式碼，因為它們是相同`reinterpret_cast`。  
  
 編譯器和執行階段也會執行隱含轉型，例如，當實值類型或內建類型當做引數傳遞給參數類型為 `Object^`的方法時，所進行的 boxing 作業。 理論上，隱含轉型不應該在執行階段造成例外狀況。如果編譯器無法執行隱含轉換，則會在編譯時期引發錯誤。  
  
Windows 執行階段是 COM 抽象概念，它會使用 HRESULT 錯誤碼，而不是例外狀況。 一般而言， [Platform::InvalidCastException](../cppcx/platform-invalidcastexception-class.md) 表示 E_NOINTERFACE 的低階 COM 錯誤。  
  
## <a name="staticcast"></a>static_cast  
 編譯時期會檢查 `static_cast` ，以判斷兩個類型之間是否有繼承關係。 如果這兩個類型不相關，則轉型會造成編譯器錯誤。  
  
 在 ref 類別上執行 `static_cast` ，會導致執行階段檢查。 ref 類別中的 `static_cast` 雖然通過編譯時期驗證，但是仍然可能會在執行階段失敗，在此情況下會擲回 `Platform::InvalidCastException` 。 一般而言，您不必處理這些例外狀況，因為這些例外狀況幾乎都表示可在開發和測試階段排除的程式設計錯誤。  
  
 如果程式碼明確宣告兩個類型之間的關聯性，因此您確定轉型應該會成功，請使用 `static_cast` 。  
  
```
    interface class A{};  
    public ref class Class1 sealed : A { };  
...  
    A^ obj = ref new Class1(); // Class1 is an A  
    // You know obj is a Class1. The compiler verifies that this is possible, and in C++/CX a run-time check is also performed.  
    Class1^ c = static_cast<Class1^>(obj);
```  
  
## <a name="safecast"></a>safe_cast  
 `safe_cast`運算子是部分 ofWindows 執行階段。 它會執行執行階段類型檢查，並在轉換失敗時擲回 `Platform::InvalidCastException` 。 當執行階段失敗表示例外狀況時，請使用 `safe_cast` 。 `safe_cast` 的主要目的是為了在其發生的開發和測試階段協助識別程式設計錯誤。 您不必處理此例外狀況，因為未處理的例外狀況本身會識別失敗點。  
  
 如果程式碼未宣告關聯性，但是您確定轉型應該會成功，請使用 safe_cast。  
  
```  
    // A and B are not related  
    interface class A{};  
    interface class B{};  
    public ref class Class1 sealed : A, B { };  
...  
    A^ obj = ref new Class1();  
  
    // You know that obj’s backing type implements A and B, but  
    // the compiler can’t tell this by comparing A and B. The run-time type check succeeds.  
    B^ obj2 = safe_cast<B^>(obj);  
```  
  
## <a name="dynamiccast"></a>dynamic_cast  
 使用`dynamic_cast`當您將物件轉型 (更明確地說，也就是 hat `^`) 衍生程度較大的類型，您會預期目標物件有時可能會是`nullptr`或轉型可能會失敗，而且您想要處理該條件當做正常程式碼路徑而非例外狀況。 例如，在**空白應用程式 (通用 Windows)** 專案範本`OnLaunched`方法中的`app.xamp.cpp`使用`dynamic_cast`來測試應用程式視窗是否有內容。 如果它沒有內容也並非錯誤，因為這是預期的情況。 `Windows::Current::Content` 是 `Windows::UI::XAML::UIElement` 並且會轉換為 `Windows::UI.XAML::Controls::Frame`，這在繼承階層架構中是屬於衍生程度較高的類型。  
```
void App::OnLaunched(Windows::ApplicationModel::Activation::LaunchActivatedEventArgs^ args)  
{  
    auto rootFrame = dynamic_cast<Frame^>(Window::Current->Content);  
  
    // Do not repeat app initialization when the window already has content,  
    // just ensure that the window is active  
    if (rootFrame == nullptr)  
    {  
        // Create a Frame to act as the navigation context and associate it with  
        // a SuspensionManager key  
        rootFrame = ref new Frame();  
...  
```  
 `dynamic_cast` 的另一個用途是探查 `Object^` 來判斷它是否包含 Boxed 實值類型。 在這種情況下，您會嘗試 `dynamic_cast<Platform::Box>` 或 `dynamic_cast<Platform::IBox>`。  
  
 **dynamic_cast 和追蹤參考 (%)**  
  
 您也可以將 `dynamic_cast` 套用至追蹤參考，不過在此情況下，轉型的行為類似於 `safe_cast`。 它會在失敗時擲回 `Platform::InvalidCastException` ，因為追蹤參考不能有 `nullptr`值。  
  
## <a name="reinterpretcast"></a>reinterpret_cast  
 我們建議您不要使用 [reinterpret_cast](../cpp/reinterpret-cast-operator.md) ，因為編譯時期檢查和執行階段檢查都不會執行。 在最糟的狀況下， `reinterpret_cast` 會讓程式設計錯誤無法在開發階段被偵測到，而且可能會對程式的行為造成微妙或災難性的錯誤。 因此，我們建議您只有在必須於不相關的類型之間轉型，而且您知道轉型將會成功的罕見情況下，才能使用 `reinterpret_cast` 。 罕見用途的範例是在其基礎 ABI 類型轉換成 Windows 執行階段類型，這表示您所採取的參考計數物件的控制。 若要這麼做，我們建議您使用 [ComPtr Class](../cpp/com-ptr-t-class.md) 智慧型指標。 否則，您必須在介面上特別呼叫 Release。 下列範例示範如何將 ref 類別轉型為 `IInspectable*`。  
  
```  
#include <wrl.h>  
using namespace Microsoft::WRL;  
auto winRtObject = ref new SomeWinRTType();  
ComPtr<IInspectable> inspectable = reinterpret_cast<IInspectable*>(winRtObject);  
...
```  
  
 如果您使用`reinterpret_cast`為轉換成不同的 oneWindows 執行階段介面，會導致要釋出，兩次的物件。 因此，只有當您轉換成非[!INCLUDE[cppwrt](../cppcx/includes/cppwrt-md.md)] 介面時，才能使用這個轉型。  
  
 **ABI 類型**  
  
-   ABI 類型存在於 Windows SDK 的標頭中。 為了方便起見，標頭會以命名空間命名，例如 `windows.storage.h`。  
  
-   ABI 類型存在於特殊命名空間 ABI 中，例如 `ABI::Windows::Storage::Streams::IBuffer*`。  
  
-   Windows 執行階段介面型別和它的對等 ABI 類型之間轉換永遠是安全 — 也就是`IBuffer^`至`ABI::IBuffer*`。  
  
-   Windows 執行階段執行階段類別永遠應該轉換為`IInspectable*`或是如果已知其預設介面。  
  
-   在轉換成 ABI 類型之後，您會擁有此類型的存留期，而且必須遵循 COM 規則。 我們建議您使用 `WRL::ComPtr` 來簡化 ABI 指標的存留期管理。  
  
 下表摘要說明可安全使用 `reinterpret_cast`的案例。 在每個案例中，雙向轉型是安全的。  
  
|||  
|-|-|  
|HSTRING|String^|  
|HSTRING*|String^*|  
|IInspectable*|Object^|  
|IInspectable**|Object^*|  
|IInspectable-derived-type*|same-interface-from-winmd^|  
|IInspectable-derived-type**|same-interface-from-winmd^*|  
|IDefault-interface-of-RuntimeClass*|same-RefClass-from-winmd^|  
|IDefault-interface-of-RuntimeClass**|same-RefClass-from-winmd^*|  
  
## <a name="see-also"></a>另請參閱  
 [類型系統](../cppcx/type-system-c-cx.md)   
 [Visual c + + 語言參考](../cppcx/visual-c-language-reference-c-cx.md)   
 [命名空間參考](../cppcx/namespaces-reference-c-cx.md)
