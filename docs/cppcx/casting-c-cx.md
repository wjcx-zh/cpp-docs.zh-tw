---
title: 轉型 (C++/CX)
ms.date: 06/19/2018
ms.assetid: 5247f6c7-6a0a-4021-97c9-21c868bd9455
ms.openlocfilehash: 5e51f9e100be2096494e10aca38232dbd1576f40
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88843478"
---
# <a name="casting-ccx"></a>轉型 (C++/CX)

有四個不同的轉換運算子適用于 Windows 執行階段類型： [Static_cast 運算子](../cpp/static-cast-operator.md)、 [dynamic_cast 運算子](../cpp/dynamic-cast-operator.md)、 **safe_cast 運算子**和 [reinterpret_cast 運算子](../cpp/reinterpret-cast-operator.md)。 **safe_cast** ，並在 **`static_cast`** 無法執行轉換時擲回例外狀況; [Static_cast 運算子](../cpp/static-cast-operator.md) 也會執行編譯時期類型檢查。 **`dynamic_cast`** 如果無法轉換型別，則會傳回 **`nullptr`** 。 雖然會傳回 **`reinterpret_cast`** 非 null 值，但可能無效。 基於這個理由，建議您不要使用， **`reinterpret_cast`** 除非您知道轉換會成功。 此外，我們建議您不要在 c + +/CX 程式碼中使用 C 樣式轉換，因為它們與相同 **`reinterpret_cast`** 。

編譯器和執行階段也會執行隱含轉型，例如，當實值類型或內建類型當做引數傳遞給參數類型為 `Object^`的方法時，所進行的 boxing 作業。 理論上，隱含轉型不應該在執行階段造成例外狀況。如果編譯器無法執行隱含轉換，則會在編譯時期引發錯誤。

Windows 執行階段是透過 COM 的抽象概念，它會使用 HRESULT 錯誤碼而非例外狀況。 一般而言， [Platform::InvalidCastException](../cppcx/platform-invalidcastexception-class.md) 表示 E_NOINTERFACE 的低階 COM 錯誤。

## <a name="static_cast"></a>static_cast

**`static_cast`** 系統會在編譯時期檢查，以判斷這兩種類型之間是否有繼承關聯性。 如果這兩個類型不相關，則轉型會造成編譯器錯誤。

**`static_cast`** Ref 類別上的 A 也會執行執行時間檢查。 **`static_cast`** Ref 類別上的 A 可以傳遞編譯時間驗證，但在執行時間仍會失敗，在此情況下 `Platform::InvalidCastException` ，會擲回。 一般而言，您不必處理這些例外狀況，因為這些例外狀況幾乎都表示可在開發和測試階段排除的程式設計錯誤。

**`static_cast`** 如果程式碼明確宣告兩種類型之間的關聯性，您就可以使用，因此您可以確定轉換是否正常運作。

```cpp
    interface class A{};
    public ref class Class1 sealed : A { };
    // ...
    A^ obj = ref new Class1(); // Class1 is an A
    // You know obj is a Class1. The compiler verifies that this is possible, and in C++/CX a run-time check is also performed.
    Class1^ c = static_cast<Class1^>(obj);
```

## <a name="safe_cast"></a>safe_cast

**Safe_cast**運算子是 Windows 執行階段的一部分。 它會執行執行階段類型檢查，並在轉換失敗時擲回 `Platform::InvalidCastException` 。 當執行時間失敗表示有例外狀況時，請使用 **safe_cast** 。 **Safe_cast**的主要目的是協助識別開發和測試階段期間發生的程式設計錯誤。 您不必處理此例外狀況，因為未處理的例外狀況本身會識別失敗點。

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

**`dynamic_cast`** 當您將物件轉型 (更明確、hat **^**) 轉換為更衍生的型別時，您預期目標物件有時可能是 **`nullptr`** 或轉換可能會失敗，而且您想要將該條件視為一般程式碼路徑而非例外狀況處理。 例如，在 ** (通用 Windows) 專案範本的空白應用程式 ** 中， `OnLaunched` xamp 中的方法會使用 **`dynamic_cast`** 測試應用程式視窗是否有內容。 如果它沒有內容也並非錯誤，因為這是預期的情況。 `Windows::Current::Content` 是 `Windows::UI::XAML::UIElement` 並且會轉換為 `Windows::UI.XAML::Controls::Frame`，這在繼承階層架構中是屬於衍生程度較高的類型。

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

的另一個用法 **`dynamic_cast`** 是探查 `Object^` ，以判斷它是否包含已裝箱的實值型別。 在這種情況下，您會嘗試 `dynamic_cast<Platform::Box>` 或 `dynamic_cast<Platform::IBox>`。

## <a name="dynamic_cast-and-tracking-references-"></a>dynamic_cast 和追蹤參考 (%)

您也可以將套用 **`dynamic_cast`** 至追蹤參考，但在此情況下，轉換的行為就像 **safe_cast**一樣。 `Platform::InvalidCastException`因為追蹤參考的值不能是，所以會在失敗時擲回 **`nullptr`** 。

## <a name="reinterpret_cast"></a>reinterpret_cast

我們建議您不要使用 [reinterpret_cast](../cpp/reinterpret-cast-operator.md) ，因為編譯時期檢查和執行階段檢查都不會執行。 在最糟的情況下，可以在 **`reinterpret_cast`** 開發期間偵測程式設計錯誤，並造成程式列為中的微妙或嚴重錯誤。 因此， **`reinterpret_cast`** 當您必須在不相關的類型之間轉換時，我們建議您只在罕見的情況下使用，而且您知道轉換會成功。 很少使用的範例是將 Windows 執行階段類型轉換成其基礎 ABI 類型，這表示您會控制物件的參考計數。 若要這麼做，我們建議您使用 [ComPtr Class](../cpp/com-ptr-t-class.md) 智慧型指標。 否則，您必須在介面上特別呼叫 Release。 下列範例示範如何將 ref 類別轉型為 `IInspectable*`。

```cpp
#include <wrl.h>
using namespace Microsoft::WRL;
auto winRtObject = ref new SomeWinRTType();
ComPtr<IInspectable> inspectable = reinterpret_cast<IInspectable*>(winRtObject);
// ...
```

如果您使用 **`reinterpret_cast`** 從 OneWindows 執行時間介面轉換成另一個介面，則會導致物件釋放兩次。 因此，當您轉換成非 C + + 元件擴充介面時，請只使用這項轉換。

## <a name="abi-types"></a>ABI 類型

- ABI 類型存在於 Windows SDK 的標頭中。 為了方便起見，標頭會以命名空間命名，例如 `windows.storage.h`。

- ABI 類型存在於特殊命名空間 ABI 中，例如 `ABI::Windows::Storage::Streams::IBuffer*`。

- Windows 執行階段介面型別與其對等 ABI 類型之間的轉換一律安全，也就是 `IBuffer^` `ABI::IBuffer*` 。

- Windows 執行階段執行時間類別應該一律轉換成 `IInspectable*` 或其預設介面（如果已知的話）。

- 在轉換成 ABI 類型之後，您會擁有此類型的存留期，而且必須遵循 COM 規則。 我們建議您使用 `WRL::ComPtr` 來簡化 ABI 指標的存留期管理。

下表摘要說明可安全使用的案例 **`reinterpret_cast`** 。 在每個案例中，雙向轉型是安全的。

| 轉換來源、轉換成 | 轉換成，轉換自 |
|--|--|
| `HSTRING` | `String^` |
| `HSTRING*` | `String^*` |
| `IInspectable*` | `Object^` |
| `IInspectable**` | `Object^*` |
| `IInspectable-derived-type*` | `same-interface-from-winmd^` |
| `IInspectable-derived-type**` | `same-interface-from-winmd^*` |
| `IDefault-interface-of-RuntimeClass*` | `same-RefClass-from-winmd^` |
| `IDefault-interface-of-RuntimeClass**` | `same-RefClass-from-winmd^*` |

## <a name="see-also"></a>另請參閱

- [型別系統](../cppcx/type-system-c-cx.md)
- [C + +/CX 語言參考](../cppcx/visual-c-language-reference-c-cx.md)
- [命名空間參考](../cppcx/namespaces-reference-c-cx.md)
