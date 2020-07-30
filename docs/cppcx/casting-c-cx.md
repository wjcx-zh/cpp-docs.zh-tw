---
title: 轉型 (C++/CX)
ms.date: 06/19/2018
ms.assetid: 5247f6c7-6a0a-4021-97c9-21c868bd9455
ms.openlocfilehash: a51e02b59b2f7229193987f993edbccfb56b779d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233518"
---
# <a name="casting-ccx"></a>轉型 (C++/CX)

有四個不同的轉型運算子適用于 Windows 執行階段類型： [Static_cast 運算子](../cpp/static-cast-operator.md)、 [dynamic_cast 運算子](../cpp/dynamic-cast-operator.md)、 **safe_cast 運算子**和[reinterpret_cast 運算子](../cpp/reinterpret-cast-operator.md)。 **safe_cast** ，並 **`static_cast`** 在無法執行轉換時擲回例外狀況;[Static_cast 運算子](../cpp/static-cast-operator.md)也會執行編譯時期類型檢查。 **`dynamic_cast`****`nullptr`** 如果無法轉換類型，則傳回。 雖然會傳回 **`reinterpret_cast`** 非 null 值，但它可能無效。 基於這個理由，我們建議您不要使用， **`reinterpret_cast`** 除非您知道轉換將會成功。 此外，我們建議您不要在 c + +/CX 程式碼中使用 C 樣式的轉換，因為它們與相同 **`reinterpret_cast`** 。

編譯器和執行階段也會執行隱含轉型，例如，當實值類型或內建類型當做引數傳遞給參數類型為 `Object^`的方法時，所進行的 boxing 作業。 理論上，隱含轉型不應該在執行階段造成例外狀況。如果編譯器無法執行隱含轉換，則會在編譯時期引發錯誤。

Windows 執行階段是 COM 的抽象概念，它會使用 HRESULT 錯誤碼而不是例外狀況。 一般而言， [Platform::InvalidCastException](../cppcx/platform-invalidcastexception-class.md) 表示 E_NOINTERFACE 的低階 COM 錯誤。

## <a name="static_cast"></a>static_cast

**`static_cast`** 會在編譯時期檢查，以判斷兩個類型之間是否有繼承關聯性。 如果這兩個類型不相關，則轉型會造成編譯器錯誤。

**`static_cast`** Ref 類別上的也會導致執行執行時間檢查。 **`static_cast`** Ref 類別上的可以通過編譯時間驗證，但是在執行時間仍然失敗; 在此情況下 `Platform::InvalidCastException` ，會擲回。 一般而言，您不必處理這些例外狀況，因為這些例外狀況幾乎都表示可在開發和測試階段排除的程式設計錯誤。

**`static_cast`** 如果程式碼明確宣告這兩個類型之間的關聯性，而且您確定轉換應該有效，請使用。

```cpp
    interface class A{};
    public ref class Class1 sealed : A { };
    // ...
    A^ obj = ref new Class1(); // Class1 is an A
    // You know obj is a Class1. The compiler verifies that this is possible, and in C++/CX a run-time check is also performed.
    Class1^ c = static_cast<Class1^>(obj);
```

## <a name="safe_cast"></a>safe_cast

**Safe_cast**運算子是 Windows 執行階段的一部分。 它會執行執行階段類型檢查，並在轉換失敗時擲回 `Platform::InvalidCastException` 。 當執行時間失敗表示例外狀況時，請使用**safe_cast** 。 **Safe_cast**的主要目的是在開發和測試階段期間，協助找出發生程式設計錯誤的時間點。 您不必處理此例外狀況，因為未處理的例外狀況本身會識別失敗點。

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

## <a name="dynamic_cast"></a>dynamic_cast

**`dynamic_cast`** 當您將物件（更具體而言，hat）轉換 **^** 成更衍生的型別時，您會預期目標物件有時可能是 **`nullptr`** 或轉換可能會失敗，而您想要將該條件當做一般程式碼路徑來處理，而不是例外狀況。 例如，在 [**空白應用程式（通用 Windows）** ] 專案範本中， `OnLaunched` xamp 中的方法會使用 **`dynamic_cast`** 測試應用程式視窗是否有內容。 如果它沒有內容也並非錯誤，因為這是預期的情況。 `Windows::Current::Content` 是 `Windows::UI::XAML::UIElement` 並且會轉換為 `Windows::UI.XAML::Controls::Frame`，這在繼承階層架構中是屬於衍生程度較高的類型。

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

的另一種用法 **`dynamic_cast`** 是探查 `Object^` ，以判斷它是否包含已裝箱的實值型別。 在這種情況下，您會嘗試 `dynamic_cast<Platform::Box>` 或 `dynamic_cast<Platform::IBox>`。

## <a name="dynamic_cast-and-tracking-references-"></a>dynamic_cast 和追蹤參考 (%)

您也可以將套用 **`dynamic_cast`** 至追蹤參考，但在此情況下，轉換的行為就像**safe_cast**。 `Platform::InvalidCastException`因為追蹤參考不能有的值，所以它會在失敗時擲回 **`nullptr`** 。

## <a name="reinterpret_cast"></a>reinterpret_cast

我們建議您不要使用 [reinterpret_cast](../cpp/reinterpret-cast-operator.md) ，因為編譯時期檢查和執行階段檢查都不會執行。 在最糟的情況下， **`reinterpret_cast`** 可讓程式設計錯誤在開發時間無法偵測到，並在您的程式列為中造成微妙或嚴重錯誤。 因此，我們建議您 **`reinterpret_cast`** 只在少數情況下，當您必須在不相關的類型之間進行轉換，而且您知道轉換會成功時，才使用。 很少使用的範例是將 Windows 執行階段類型轉換成其基礎 ABI 類型，這表示您要控制物件的參考計數。 若要這麼做，我們建議您使用 [ComPtr Class](../cpp/com-ptr-t-class.md) 智慧型指標。 否則，您必須在介面上特別呼叫 Release。 下列範例示範如何將 ref 類別轉型為 `IInspectable*`。

```cpp
#include <wrl.h>
using namespace Microsoft::WRL;
auto winRtObject = ref new SomeWinRTType();
ComPtr<IInspectable> inspectable = reinterpret_cast<IInspectable*>(winRtObject);
// ...
```

如果您使用 **`reinterpret_cast`** 從 OneWindows 執行時間介面轉換成另一個，則會導致物件釋放兩次。 因此，只有當您轉換為非 C + + 元件延伸模組介面時，才使用這個轉換。

## <a name="abi-types"></a>ABI 類型

- ABI 類型存在於 Windows SDK 的標頭中。 為了方便起見，標頭會以命名空間命名，例如 `windows.storage.h`。

- ABI 類型存在於特殊命名空間 ABI 中，例如 `ABI::Windows::Storage::Streams::IBuffer*`。

- Windows 執行階段介面類別型與其對等 ABI 類型之間的轉換一律是安全的，也就 `IBuffer^` 是 `ABI::IBuffer*` 。

- Windows 執行階段執行時間類別應該一律轉換成 `IInspectable*` 或其預設介面（如果已知的話）。

- 在轉換成 ABI 類型之後，您會擁有此類型的存留期，而且必須遵循 COM 規則。 我們建議您使用 `WRL::ComPtr` 來簡化 ABI 指標的存留期管理。

下表摘要說明可安全使用的案例 **`reinterpret_cast`** 。 在每個案例中，雙向轉型是安全的。

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

- [型別系統](../cppcx/type-system-c-cx.md)
- [C + +/CX 語言參考](../cppcx/visual-c-language-reference-c-cx.md)
- [命名空間參考](../cppcx/namespaces-reference-c-cx.md)
