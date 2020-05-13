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
ms.openlocfilehash: 6b57366df5f466ffe49e4c0b46e05b1eed515535
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032482"
---
# <a name="threading-and-marshaling-ccx"></a>執行緒和封送處理 (C++/CX)

在絕大多數情況下,可以從任何線程訪問 Windows 運行時類的實例,如標準C++物件。 這類類別都稱為 "Agile"。 但是,隨 Windows 附帶的少量 Windows 運行時類是非敏捷的,並且必須使用與標準 C++物件更像 COM 物件的類。 您不必非常了解 COM 才能使用非 agile 的類別，但是必須將類別的執行緒模型及其封送處理行為納入考量。 針對這些必須使用非 Agile 類別之執行個體的少見情況，本文將提供背景知識和指引供您參考。

## <a name="threading-model-and-marshaling-behavior"></a>執行緒模型和封送處理行為

Windows 執行時類可以通過多種方式支援併發線程訪問,這由應用於它的兩個屬性指示:

- `ThreadingModel` 屬性可具有 `ThreadingModel` 列舉所定義的其中一個值：STA、MTA 或 Both。

- `MarshallingBehavior` 屬性可具有 `MarshallingType` 列舉所定義的其中一個值：Agile、None 或 Standard。

`ThreadingModel` 屬性可指定類別在啟用時的載入位置：只在使用者介面執行緒 (STA) 內容中、只在背景執行緒 (MTA) 內容中，或者在建立物件之執行緒 (兩者) 的內容中。 `MarshallingBehavior` 屬性值表示各種執行緒內容中的物件行為，在一般情況下您無需深入了解這些值。  在 Windows 應用程式開發介面所提供的類別中，約有 90% 具有 `ThreadingModel`=Both 與 `MarshallingType`=Agile。 這表示它們可以明確而有效率地處理低階執行緒的詳細資料。   當您使用 `ref new` 建立 "agile" 類別時，您可以從您的主要應用程式執行緒或從一或多個背景工作執行緒呼叫此類別的相關方法。  換句話說，您可以從您程式碼中的任一處使用 Agile 類別，無論它是由 Windows 還是協力廠商所提供。 您無需顧慮類別的執行緒模型或封送處理行為。

## <a name="consuming-windows-runtime-components"></a>使用 Windows 執行時元件

創建通用 Windows 平台應用時,可能會與敏捷和非敏捷元件進行交互。 當您與非 Agile 元件互動時，可能會出現下列警告。

### <a name="compiler-warning-c4451-when-consuming-non-agile-classes"></a>使用非敏捷類時,編譯器警告 C4451

基於多種原因，有些類別不可以是 Agile。 如果您要同時從使用者介面執行緒與背景執行緒存取非 Agile 類別的執行個體，請格外謹慎以確保在執行階段能有正確的行為。 當您在全域作用域中實例化應用中的非敏捷運行時類,或將非敏捷類型聲明為 ref 類中的類成員時,Microsoft C++編譯器發出警告,該類本身被標記為敏捷。

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

當您將參考 (在成員範圍或全域範圍) 新增至具有封送處理行為 "Standard" 的物件時，編譯器會發出警告，建議您將型别封裝在 `Platform::Agile<T>`中。 `Consider using 'Platform::Agile<Windows::Security::Credentials::UI::CredentialPickerOptions>' instead` 如果您使用 `Agile<T>`，即可像任何其他 Agile 類別一樣使用該類別。 在下列情況下，請使用 `Platform::Agile<T>` ：

- 在全域範圍中宣告了非 Agile 變數。

- 在類別範圍中宣告了非 Agile 變數，且使用的程式碼有可能挾帶指標，也就是未經正確的封送處理即將其用於不同的 Apartment。

如果您的情況不屬於上述兩者，則可以將包含類別標記為非 Agile。 換句話說,您應該僅在非敏捷類中直接保存非敏捷物件,並通過 Platform::agile\<T>在敏捷類中保存非敏捷物件。

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

當您建立對具有「無」 封送行為的 proc Windows 執行時類別的參考時,編譯器會發出警告 C4451,但`Platform::Agile<T>`不建議您考慮使用 。  除了此警告外，編譯器無法提供進一歩的協助，因此您必須正確使用類別，並確保您的程式碼只會從使用者介面執行緒呼叫 STA 元件，從背景執行緒呼叫 MTA 元件。

## <a name="authoring-agile-windows-runtime-components"></a>編寫敏捷 Windows 執行時元件

當您在C++/CX 中定義 ref 類時,默認情況下它是敏捷的,`ThreadingModel`也就是說`MarshallingType`,它有 #两个 和 =敏捷。  如果使用 Windows 運行時 C++範本庫,則可以`FtmBase`通過派生 使用 派`FreeThreadedMarshaller`生使類變得靈活。  如果您撰寫具有 `ThreadingModel`=Both 或 `ThreadingModel`=MTA 的類別，請確定該類別具備執行緒安全。

您可以修改 ref 類別的執行緒模型和封送處理行為。 但是，如果您進行變更而使其成為非 Agile 類別，您必須了解這些變更的相關影響。

下面的範例展示如何在 Windows`MarshalingBehavior``ThreadingModel`執行時 類庫中將和屬性應用於運行時類。 當應用程式使用 DLL 與 `ref new` 關鍵字啟動 `MySTAClass` 類別物件時，該物件將會在單一執行緒 Apartment 中啟動，且不支援封送處理。

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

第三方 Windows 運行時元件所需的線程和封送資訊在元件的應用清單註冊資訊中指定。 我們建議您使所有 Windows 運行時元件都變得靈活。 這可確保用戶端程式碼能夠從應用程式中的任何執行緒呼叫您的元件，並且可改善這些呼叫的效能，因為這些都是沒有封送處理的直接呼叫。 如果您以這種方式撰寫類別，則用戶端程式碼無需 `Platform::Agile<T>` 即可使用您的類別。

## <a name="see-also"></a>另請參閱

[ThreadingModel](/uwp/api/windows.foundation.metadata.threadingmodel)<br/>
[MarshallingBehavior](/uwp/api/windows.foundation.metadata.marshalingbehaviorattribute)
