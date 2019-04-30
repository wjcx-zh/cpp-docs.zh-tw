---
title: 執行緒和封送處理 (C++/CX)
ms.date: 12/30/2016
f1_keywords:
- C4451
helpviewer_keywords:
- threading issues, C++/CX
- agility, C++/CX
- C++/CX, threading issues
ms.assetid: 83e9ca1d-5107-4194-ae6f-e01bd928c614
ms.openlocfilehash: c5bce60e564bef490bcfafd6f8559dffe5fd4f1d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404633"
---
# <a name="threading-and-marshaling-ccx"></a>執行緒和封送處理 (C++/CX)

在大部分情況下，Windows 執行階段類別的執行個體像標準C++物件，可以從任何執行緒存取。 這類類別都稱為 "Agile"。 不過，少數隨附於 Windows 的 Windows 執行階段類別的非 agile，而且僅必須比標準的 COM 物件一樣多取用C++物件。 您不必非常了解 COM 才能使用非 agile 的類別，但是必須將類別的執行緒模型及其封送處理行為納入考量。 針對這些必須使用非 Agile 類別之執行個體的少見情況，本文將提供背景知識和指引供您參考。

## <a name="threading-model-and-marshaling-behavior"></a>執行緒模型和封送處理行為

Windows 執行階段類別可以各種方式支援並行執行緒存取，會套用至它的兩個屬性所示：

- `ThreadingModel` 屬性可具有 `ThreadingModel` 列舉所定義的其中一個值：STA、MTA 或 Both。

- `MarshallingBehavior` 屬性可具有 `MarshallingType` 列舉所定義的其中一個值：Agile、None 或 Standard。

`ThreadingModel` 屬性可指定類別在啟用時的載入位置：只在使用者介面執行緒 (STA) 內容中、只在背景執行緒 (MTA) 內容中，或者在建立物件之執行緒 (兩者) 的內容中。 `MarshallingBehavior` 屬性值表示各種執行緒內容中的物件行為，在一般情況下您無需深入了解這些值。  在 Windows 應用程式開發介面所提供的類別中，約有 90% 具有 `ThreadingModel`=Both 與 `MarshallingType`=Agile。 這表示它們可以明確而有效率地處理低階執行緒的詳細資料。   當您使用 `ref new` 建立 "agile" 類別時，您可以從您的主要應用程式執行緒或從一或多個背景工作執行緒呼叫此類別的相關方法。  換句話說，您可以從您程式碼中的任一處使用 Agile 類別，無論它是由 Windows 還是協力廠商所提供。 您無需顧慮類別的執行緒模型或封送處理行為。

## <a name="consuming-windows-runtime-components"></a>使用 Windows 執行階段元件

當您建立通用 Windows 平台應用程式時，可能會與 agile 和非 agile 元件互動。 當您與非 Agile 元件互動時，可能會出現下列警告。

### <a name="compiler-warning-c4451-when-consuming-non-agile-classes"></a>編譯器警告 C4451，使用非 agile 類別時

基於多種原因，有些類別不可以是 Agile。 如果您要同時從使用者介面執行緒與背景執行緒存取非 Agile 類別的執行個體，請格外謹慎以確保在執行階段能有正確的行為。 當您在全域範圍中使用您的應用程式具現化非 Agile 執行階段類別時，或將非 Agile 型别宣告為本身標示為 Agile 之 ref 類別中的類別成員時，Visual C++ 編譯器將會發出警告。

在非 Agile 類別中，最容易處理的是具有 `ThreadingModel`=Both 與 `MarshallingType`=Standard 的類別。  您只要使用 `Agile<T>` 協助程式類別，即可將這些類別設定成 Agile 類別。   下列範例說明類型 `Windows::Security::Credentials::UI::CredentialPickerOptions^`的非 Agile 物件宣告，以及因此而發出的編譯器警告。

```

ref class MyOptions
    {
    public:
        property Windows::Security::Credentials::UI::CredentialPickerOptions^ Options

        {
            Windows::Security::Credentials::UI::CredentialPickerOptions^ get()
            {
                return _myOptions;
            }
        }
    private:
        Windows::Security::Credentials::UI::CredentialPickerOptions^ _myOptions;
    };
```

發出的警告如下：

> `Warning 1 warning C4451: 'Platform::Agile<T>::_object' : Usage of ref class 'Windows::Security::Credentials::UI::CredentialPickerOptions' inside this context can lead to invalid marshaling of object across contexts. Consider using 'Platform::Agile<Windows::Security::Credentials::UI::CredentialPickerOptions>' instead`

當您加入的參考，在成員範圍或全域範圍，來封送處理行為"Standard"的物件，編譯器會發出警告，提醒您包裝中的型別`Platform::Agile<T>`:`Consider using 'Platform::Agile<Windows::Security::Credentials::UI::CredentialPickerOptions>' instead` 如果您使用`Agile<T>`，像任何其他 agile 類別一樣，您可以使用此類別。 在下列情況下，請使用 `Platform::Agile<T>` ：

- 在全域範圍中宣告了非 Agile 變數。

- 在類別範圍中宣告了非 Agile 變數，且使用的程式碼有可能挾帶指標，也就是未經正確的封送處理即將其用於不同的 Apartment。

如果您的情況不屬於上述兩者，則可以將包含類別標記為非 Agile。 換句話說，您應該直接保留非 agile 物件只能在非 agile 類別，並保留非 agile 物件，透過 platform:: agile\<T > 在 agile 類別中。

下列範例示範如何使用 `Agile<T>` ，如此您就可以放心忽略該警告。

```

#include <agile.h>
ref class MyOptions
    {
    public:
        property Windows::Security::Credentials::UI::CredentialPickerOptions^ Options

        {
            Windows::Security::Credentials::UI::CredentialPickerOptions^ get()
            {
                return m_myOptions.Get();
            }
        }
    private:
        Platform::Agile<Windows::Security::Credentials::UI::CredentialPickerOptions^> m_myOptions;

    };
```

需留意到 `Agile` 無法做為 ref 類別中的傳回值或參數。 `Agile<T>::Get()` 方法會傳回您可以在公用方法或屬性中跨應用程式二進位介面 (ABI) 傳遞的物件的控制代碼 (^)。

在視覺效果C++，當您建立具有封送處理行為"None"，則編譯器將發出警告 C4451，但不建議您考慮使用跨處理序 Windows 執行階段類別的參考`Platform::Agile<T>`。  除了此警告外，編譯器無法提供進一歩的協助，因此您必須正確使用類別，並確保您的程式碼只會從使用者介面執行緒呼叫 STA 元件，從背景執行緒呼叫 MTA 元件。

## <a name="authoring-agile-windows-runtime-components"></a>撰寫 agile 的 Windows 執行階段元件

當您定義中的 ref 類別C++/CX，它是預設敏捷式軟體開發 — 也就是它具有`ThreadingModel`= Both 和`MarshallingType`= Agile。  如果您使用 Windows 執行階段C++樣板程式庫，您可以將您的類別敏捷式軟體開發藉由衍生自`FtmBase`，它會使用`FreeThreadedMarshaller`。  如果您撰寫具有 `ThreadingModel`=Both 或 `ThreadingModel`=MTA 的類別，請確定該類別具備執行緒安全。

您可以修改 ref 類別的執行緒模型和封送處理行為。 但是，如果您進行變更而使其成為非 Agile 類別，您必須了解這些變更的相關影響。

下列範例示範如何套用`MarshalingBehavior`和`ThreadingModel`Windows 執行階段類別庫中的執行階段類別的屬性。 當應用程式使用 DLL 與 `ref new` 關鍵字啟動 `MySTAClass` 類別物件時，該物件將會在單一執行緒 Apartment 中啟動，且不支援封送處理。

```
using namespace Windows::Foundation::Metadata;
using namespace Platform;

[Threading(ThreadingModel::STA)]
[MarshalingBehavior(MarshalingType::None)]
public ref class MySTAClass
{
};
```

非密封的類別必須要有執行緒和封送處理屬性設定，讓編譯器能夠對這些屬性具有相同值的衍生類別進行驗證。 如果類別沒有明確設定這些項目，編譯器即會產生錯誤而無法編譯。 任何從非密封的類別衍生的類別，在下列任一情況下都會產生編譯器錯誤：

- `ThreadingModel` 和 `MarshallingBehavior` 屬性未定義於衍生類別中。

- 衍生類別中的 `ThreadingModel` 和 `MarshallingBehavior` 屬性值與基底類別中的值不相符。

元件的應用程式資訊清單註冊資訊中指定的執行緒與封送處理由協力廠商 Windows 執行階段元件所需的資訊。 我們建議您所有的 Windows 執行階段元件敏捷式軟體開發。 這可確保用戶端程式碼能夠從應用程式中的任何執行緒呼叫您的元件，並且可改善這些呼叫的效能，因為這些都是沒有封送處理的直接呼叫。 如果您以這種方式撰寫類別，則用戶端程式碼無需 `Platform::Agile<T>` 即可使用您的類別。

## <a name="see-also"></a>另請參閱

[ThreadingModel](/uwp/api/Windows.Foundation.Metadata.ThreadingModel)<br/>
[MarshallingBehavior](/uwp/api/windows.foundation.metadata.marshalingbehaviorattribute)
