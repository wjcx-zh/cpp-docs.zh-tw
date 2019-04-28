---
title: 轉型 (C++/CX)
ms.date: 06/19/2018
ms.assetid: 5247f6c7-6a0a-4021-97c9-21c868bd9455
ms.openlocfilehash: 65d489d14c91b462e5a2bbe8bd60fce2657904a7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62258209"
---
# <a name="casting-ccx"></a>轉型 (C++/CX)

四個不同的轉換運算子套用至 Windows 執行階段型別： [static_cast 運算子](../cpp/static-cast-operator.md)， [dynamic_cast 運算子](../cpp/dynamic-cast-operator.md)， **safe_cast 運算子**，和[reinterpret_cast 運算子](../cpp/reinterpret-cast-operator.md)。 **safe_cast**並**static_cast**擲回例外狀況，無法執行轉換;[static_cast 運算子](../cpp/static-cast-operator.md)也可以執行編譯時期類型檢查。 **dynamic_cast**會傳回**nullptr**如果它無法將類型轉換。 雖然**reinterpret_cast**傳回非 null 值，但是可能無效。 基於這個理由，我們建議您不要使用**reinterpret_cast**除非您知道轉型將會成功。 此外，我們建議您不要使用中的 c-style 轉換您C++/CX 程式碼，因為它們是相同**reinterpret_cast**。

編譯器和執行階段也會執行隱含轉型，例如，當實值類型或內建類型當做引數傳遞給參數類型為 `Object^`的方法時，所進行的 boxing 作業。 理論上，隱含轉型不應該在執行階段造成例外狀況。如果編譯器無法執行隱含轉換，則會在編譯時期引發錯誤。

Windows 執行階段是 COM，而不是例外狀況會使用 HRESULT 錯誤碼的抽象概念。 一般而言， [Platform::InvalidCastException](../cppcx/platform-invalidcastexception-class.md) 表示 E_NOINTERFACE 的低階 COM 錯誤。

## <a name="staticcast"></a>static_cast

A **static_cast**已在編譯時期，若要判斷兩個類型之間是否有繼承關聯性。 如果這兩個類型不相關，則轉型會造成編譯器錯誤。

A **static_cast** ref 類別也會使執行階段檢查，以執行。 A **static_cast** ref 類別可以通過編譯時期驗證，但仍然失敗，在執行階段; 在此案例`Platform::InvalidCastException`就會擲回。 一般而言，您不必處理這些例外狀況，因為這些例外狀況幾乎都表示可在開發和測試階段排除的程式設計錯誤。

使用**static_cast**如果程式碼明確宣告的兩個類型之間的關聯性，因此就確定轉型應該會成功。

```cpp
    interface class A{};
    public ref class Class1 sealed : A { };
    // ...
    A^ obj = ref new Class1(); // Class1 is an A
    // You know obj is a Class1. The compiler verifies that this is possible, and in C++/CX a run-time check is also performed.
    Class1^ c = static_cast<Class1^>(obj);
```

## <a name="safecast"></a>safe_cast

**Safe_cast**運算子是 Windows 執行階段的一部分。 它會執行執行階段類型檢查，並在轉換失敗時擲回 `Platform::InvalidCastException` 。 使用**safe_cast**當執行階段發生失敗表示例外狀況。 主要用途**safe_cast**是要協助識別程式設計錯誤開發和測試其發生之處的階段。 您不必處理此例外狀況，因為未處理的例外狀況本身會識別失敗點。

如果程式碼未宣告關聯性，但是您確定轉型應該會成功，請使用 safe_cast。

```cpp
    // A and B are not related
    interface class A{};
    interface class B{};
    public ref class Class1 sealed : A, B { };
    // ...
    A^ obj = ref new Class1();

    // You know that obj’s backing type implements A and B, but
    // the compiler can’t tell this by comparing A and B. The run-time type check succeeds.
    B^ obj2 = safe_cast<B^>(obj);
```

## <a name="dynamiccast"></a>dynamic_cast

使用**dynamic_cast**當您將物件轉型 (更具體來說，也就是 hat **^**) 成衍生程度較大的類型，您會預期目標物件有時可能**nullptr**或轉型可能會失敗，且您想要為一般的程式碼路徑，而不是例外狀況處理該條件。 例如，在**空白應用程式 (通用 Windows)** 專案範本`OnLaunched`app.xamp.cpp 使用方法**dynamic_cast**來測試應用程式視窗是否有內容。 如果它沒有內容也並非錯誤，因為這是預期的情況。 `Windows::Current::Content` 是 `Windows::UI::XAML::UIElement` 並且會轉換為 `Windows::UI.XAML::Controls::Frame`，這在繼承階層架構中是屬於衍生程度較高的類型。

```cpp
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
        // ...
    }
}
```

另一個用法**dynamic_cast**是探查`Object^`來判斷它是否包含 boxed 實的值類型。 在這種情況下，您會嘗試 `dynamic_cast<Platform::Box>` 或 `dynamic_cast<Platform::IBox>`。

## <a name="dynamiccast-and-tracking-references-"></a>dynamic_cast 和追蹤參考 (%)

您也可以套用**dynamic_cast**給追蹤參考，但在此情況下轉換，行為類似**safe_cast**。 它會擲回`Platform::InvalidCastException`失敗因為追蹤參考不能有值為**nullptr**。

## <a name="reinterpretcast"></a>reinterpret_cast

我們建議您不要使用 [reinterpret_cast](../cpp/reinterpret-cast-operator.md) ，因為編譯時期檢查和執行階段檢查都不會執行。 在最糟的情況下， **reinterpret_cast**可讓程式設計錯誤無法在開發期間不會偵測到與您的程式行為造成微妙或災難性的錯誤。 因此，我們建議您改用**reinterpret_cast**只有在罕見情況下必須不相關的類型之間進行轉換，而且您知道轉型將會成功。 罕見用途的範例是將 Windows 執行階段類型轉換為其基礎 ABI 類型 — 這表示您所採取的參考計數物件的控制項。 若要這麼做，我們建議您使用 [ComPtr Class](../cpp/com-ptr-t-class.md) 智慧型指標。 否則，您必須在介面上特別呼叫 Release。 下列範例示範如何將 ref 類別轉型為 `IInspectable*`。

```cpp
#include <wrl.h>
using namespace Microsoft::WRL;
auto winRtObject = ref new SomeWinRTType();
ComPtr<IInspectable> inspectable = reinterpret_cast<IInspectable*>(winRtObject);
// ...
```

如果您使用**reinterpret_cast**從 oneWindows 執行階段介面之間轉換，會使物件釋出，兩次。 因此，這項轉換只使用，當您想要轉換的非視覺效果C++元件延伸模組介面。

## <a name="abi-types"></a>ABI 類型

- ABI 類型存在於 Windows SDK 的標頭中。 為了方便起見，標頭會以命名空間命名，例如 `windows.storage.h`。

- ABI 類型存在於特殊命名空間 ABI 中，例如 `ABI::Windows::Storage::Streams::IBuffer*`。

- Windows 執行階段介面型別和其對等 ABI 類型之間的轉換永遠是安全 — 亦即`IBuffer^`至`ABI::IBuffer*`。

- Windows 執行階段執行階段類別永遠應該轉換成`IInspectable*`或它的預設介面，如果所知。

- 在轉換成 ABI 類型之後，您會擁有此類型的存留期，而且必須遵循 COM 規則。 我們建議您使用 `WRL::ComPtr` 來簡化 ABI 指標的存留期管理。

下表摘要說明的案例，它會安全地使用**reinterpret_cast**。 在每個案例中，雙向轉型是安全的。

|||
|-|-|
|`HSTRING`|`String^`|
|`HSTRING*`|`String^*`|
|`IInspectable*`|`Object^`|
|`IInspectable**`|`Object^*`|
|`IInspectable-derived-type*`|`same-interface-from-winmd^`|
|`IInspectable-derived-type**`|`same-interface-from-winmd^*`|
|`IDefault-interface-of-RuntimeClass*`|`same-RefClass-from-winmd^`|
|`IDefault-interface-of-RuntimeClass**`|`same-RefClass-from-winmd^*`|

## <a name="see-also"></a>另請參閱

- [類型系統](../cppcx/type-system-c-cx.md)
- [視覺化C++語言參考](../cppcx/visual-c-language-reference-c-cx.md)
- [命名空間參考](../cppcx/namespaces-reference-c-cx.md)
