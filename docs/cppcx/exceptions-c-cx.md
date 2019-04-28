---
title: 例外狀況 (C++/CX)
ms.date: 01/18/2018
ms.assetid: 6cbdc1f1-e4d7-4707-a670-86365146432f
ms.openlocfilehash: 7134cbb9e90f0355a3b2a912330027cf73876443
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301522"
---
# <a name="exceptions-ccx"></a>例外狀況 (C++/CX)

中的錯誤處理C++/CX 以例外狀況為基礎。 在最基本的層級，Windows 執行階段元件會報告錯誤當做 HRESULT 值。 在C++/CX，這些值會轉換成強型別包含 HRESULT 值和字串描述您可以透過程式設計方式存取的例外狀況。  例外狀況會實作為衍生自 `ref class` 的 `Platform::Exception`。  `Platform` 命名空間會爲最常見的 HRESULT 值定義不同的例外狀況類別，其他所有的值則透過 `Platform::COMException` 類別來報告。 所有的例外狀況類別都會有可供您擷取原始 HRESULT 的 [Exception::HResult](platform-exception-class.md#hresult) 欄位。 您也可以檢查呼叫堆疊資訊，協助找出原始來源的例外狀況，即使原始程式碼是以撰寫語言以外的其他偵錯工具中的使用者程式碼C++。

## <a name="exceptions"></a>例外狀況

在您C++程式，您可以擲回並攔截來自 Windows 執行階段作業的例外狀況，例外狀況衍生自`std::exception`，或使用者定義型別。 您有只在會跨應用程式二進位介面 (ABI) 界限，例如，當會攔截例外狀況的程式碼以 JavaScript 撰寫時所擲回 Windows 執行階段例外狀況。 當非 Windows 執行階段C++例外狀況到達 ABI 界限，例外狀況會轉譯成`Platform::FailureException`例外狀況，表示 E_FAIL HRESULT。 如需 ABI 的詳細資訊，請參閱 [Creating Windows Runtime Components in C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)。

您可以宣告[platform:: exception](platform-exception-class.md)使用其中兩個建構函式採用 HRESULT 參數或採用 HRESULT 參數和[platform:: string](platform-string-class.md)^ 可以之間傳遞的參數會處理它的任何 Windows 執行階段應用程式的 ABI。 或者，您可以透過採用 HRESULT 參數或採用 HRESULT 參數和 [參數的兩個](platform-exception-class.md#createexception) Exception::CreateException 方法 `Platform::String^` 多載之一，來宣告例外狀況。

## <a name="standard-exceptions"></a>標準例外狀況

C++/CX 支援標準代表一般 HRESULT 錯誤的例外狀況的集合。 每個標準例外狀況皆衍生自 [Platform::COMException](platform-comexception-class.md)，而後者又衍生自 `Platform::Exception`。 當您擲回跨 ABI 界限的例外狀況時，您必須擲回其中一個標準例外狀況。

您無法從 `Platform::Exception`衍生您自己的例外狀況型別。 若要擲回自訂例外狀況，請透過使用者定義的 HRESULT 來建構 `COMException` 物件。

下表列出標準例外狀況。

|名稱|基礎 HRESULT|描述|
|----------|------------------------|-----------------|
|COMException|*使用者定義的 HRESULT*|在 COM 方法呼叫傳回無法辨認的 HRESULT 時擲回。|
|AccessDeniedException|E\_ACCESSDENIED|在存取資源或功能遭拒時擲回。|
|ChangedStateException|電子\_CHANGED\_狀態|在父集合變更後呼叫集合迭代器或集合檢視的方法時擲回，藉以讓該方法的結果失效。|
|ClassNotRegisteredException|REGDB\_E\_CLASSNOTREG|在 COM 類別未登錄時擲回。|
|DisconnectedException|RPC\_E\_已中斷連線|在物件與用戶端的連接中斷時擲回。|
|FailureException|E\_失敗|在作業失敗時擲回。|
|InvalidArgumentException|E\_INVALIDARG|在其中一個提供給方法的引數無效時擲回。|
|InvalidCastException|E\_NOINTERFACE|在類型無法轉換成另一種類型時擲回。|
|NotImplementedException|E\_NOTIMPL|在介面方法未於類別上實作時擲回。|
|NullReferenceException|E\_指標|在嘗試解除 Null 物件的參考時擲回。|
|ObjectDisposedException|RO\_E\_已關閉|在已處置的物件上執行作業時擲回。|
|OperationCanceledException|E\_中止|在作業中止時擲回。|
|OutOfBoundsException|E\_界限|在作業嘗試存取有效範圍以外的資料時擲回。|
|OutOfMemoryException|E\_OUTOFMEMORY|在沒有足夠的記憶體可完成作業時擲回。|
|WrongThreadException|RPC\_電子\_錯誤\_執行緒|在執行緒透過不屬於其 Apartment 之 Proxy 物件的介面指標進行呼叫時擲回。|

## <a name="hresult-and-message-properties"></a>HResult 屬性與 Message 屬性

所有例外狀況都有 [HResult](platform-comexception-class.md#hresult) 屬性和 [Message](platform-comexception-class.md#message) 屬性。 [Exception::HResult](platform-exception-class.md#hresult) 屬性會取得例外狀況的基礎數值 HRESULT 值。 [Exception::Message](platform-exception-class.md#message) 屬性會取得系統提供用以說明例外狀況的字串。 在 Windows 8 中，訊息僅適用於偵錯工具，而且是唯讀狀態。 這表示當您重新擲回例外狀況時，無法加以變更。 在 Windows 8.1 中，如果重新擲回例外狀況，可以透過程式設計方式存取訊息字串並提供新的訊息。 偵錯工具中也提供更好的呼叫堆疊資訊，包括非同步方法呼叫的呼叫堆疊。

### <a name="examples"></a>範例

此範例示範如何擲回同步作業的 Windows 執行階段例外狀況：

[!code-cpp[cx_exceptions#01](codesnippet/CPP/exceptiontest/class1.cpp#01)]

下一個範例說明如何攔截例外狀況。

[!code-cpp[cx_exceptions#02](codesnippet/CPP/exceptiontest/class1.cpp#02)]

若要攔截非同步作業期間所擲回的例外狀況，使用工作類別並新增錯誤處理接續工作。 錯誤處理接續工作會將其他執行緒上擲回的例外狀況封送回呼叫端執行緒，讓您在程式碼中的單一位置上即可處理所有可能的例外狀況。 如需詳細資訊，請參閱 [使用 C++ 進行非同步程式設計](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps)。

## <a name="unhandlederrordetected-event"></a>UnhandledErrorDetected 事件

在 Windows 8.1 中，您可以訂閱以[unhandlederrordetected](/uwp/api/windows.applicationmodel.core.icoreapplicationunhandlederror#Windows_ApplicationModel_Core_ICoreApplicationUnhandledError_UnhandledErrorDetected)靜態事件，可讓您存取即將使處理序當機的未處理錯誤。 不論錯誤源自何處，它都會以透過事件引數傳入的 [Windows::ApplicationModel::Core::UnhandledError](/uwp/api/windows.applicationmodel.core.unhandlederror) 物件形式，到達這個處理常式。 當您針對物件呼叫 `Propagate` 時，它會建立及擲回對應至錯誤代碼類型的 `Platform::*Exception` 。 在 Catch 區塊，您可以視需要儲存使用者狀態，然後透過呼叫 `throw`允許處理序結束，或是執行某個動作，讓程式回到已知狀態。 下列範例示範基本模式：

在 app.xaml.h:

```cpp
void OnUnhandledException(Platform::Object^ sender, Windows::ApplicationModel::Core::UnhandledErrorDetectedEventArgs^ e);
```

在 app.xaml.cpp:

```cpp
// Subscribe to the event, for example in the app class constructor:
Windows::ApplicationModel::Core::CoreApplication::UnhandledErrorDetected += ref new EventHandler<UnhandledErrorDetectedEventArgs^>(this, &App::OnUnhandledException);

// Event handler implementation:
void App::OnUnhandledException(Platform::Object^ sender, Windows::ApplicationModel::Core::UnhandledErrorDetectedEventArgs^ e)
{
    auto err = e->UnhandledError;

    if (!err->Handled) //Propagate has not been called on it yet.
{
    try
    {
        err->Propagate();
    }
    // Catch any specific exception types if you know how to handle them
    catch (AccessDeniedException^ ex)
    {
        // TODO: Log error and either take action to recover
        // or else re-throw exception to continue fail-fast
    }
}
```

### <a name="remarks"></a>備註

C++/CX 不會使用`finally`子句。

## <a name="see-also"></a>另請參閱

[視覺化C++語言參考](visual-c-language-reference-c-cx.md)<br/>
[命名空間參考](namespaces-reference-c-cx.md)
