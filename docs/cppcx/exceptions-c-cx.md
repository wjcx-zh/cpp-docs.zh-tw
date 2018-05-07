---
title: 例外狀況 (C + + /CX) |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2018
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 6cbdc1f1-e4d7-4707-a670-86365146432f
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5e58ad68f4cfc7d514c4d8434cf52f6d348640c4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="exceptions-ccx"></a>例外狀況 (C++/CX)

錯誤處理以 C + + /CX 根據例外狀況。 在最基本的層級，Windows 執行階段元件會報告錯誤，在以 HRESULT 值。 在 C + + /CX 中，這些值會轉換成包含 HRESULT 值和字串說明您可以透過程式設計方式存取的強類型例外狀況。  例外狀況會實作為衍生自 `ref class` 的 `Platform::Exception`。  `Platform` 命名空間會爲最常見的 HRESULT 值定義不同的例外狀況類別，其他所有的值則透過 `Platform::COMException` 類別來報告。 所有的例外狀況類別都會有可供您擷取原始 HRESULT 的 [Exception::HResult](platform-exception-class.md#hresult) 欄位。 您也可以檢查使用者程式碼，協助找出原始的例外狀況，即使原始程式碼以 c + + 以外的語言撰寫的程式碼中偵錯工具中的呼叫堆疊資訊。

## <a name="exceptions"></a>例外狀況

在 c + + 程式中，您可以擲回並攔截來自 Windows 執行階段作業的例外狀況，例外狀況衍生自`std::exception`，或使用者定義型別。 您必須擲回 Windows 執行階段例外狀況，才會跨應用程式二進位介面 (ABI) 界限，比方說，以 JavaScript 撰寫的程式碼攔截例外狀況時。 當非 Windows 執行階段 c + + 例外狀況到達 ABI 界限時，會轉譯成`Platform::FailureException`例外狀況，表示 E_FAIL HRESULT。 如需 ABI 的詳細資訊，請參閱[c + + 中建立 Windows 執行階段元件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)。

您可以宣告[platform:: exception](platform-exception-class.md)透過採用 HRESULT 參數或採用 HRESULT 參數的兩個建構函式和[platform:: string](platform-string-class.md)^ 可以之間傳遞的參數ABI 到任何 Windows 執行階段應用程式會處理它。 或者，您可以透過採用 HRESULT 參數或採用 HRESULT 參數和 [參數的兩個](platform-exception-class.md#createexception) Exception::CreateException 方法 `Platform::String^` 多載之一，來宣告例外狀況。

## <a name="standard-exceptions"></a>標準例外狀況

C + + /CX 支援一組代表一般 HRESULT 錯誤的標準例外狀況。 每個標準例外狀況皆衍生自 [Platform::COMException](platform-comexception-class.md)，而後者又衍生自 `Platform::Exception`。 當您擲回跨 ABI 界限的例外狀況時，您必須擲回其中一個標準例外狀況。

您無法從 `Platform::Exception`衍生您自己的例外狀況型別。 若要擲回自訂例外狀況，請透過使用者定義的 HRESULT 來建構 `COMException` 物件。

下表列出標準例外狀況。

|名稱|基礎 HRESULT|描述|
|----------|------------------------|-----------------|
|COMException|*使用者定義的 HRESULT*|在 COM 方法呼叫傳回無法辨認的 HRESULT 時擲回。|
|AccessDeniedException|E\_ACCESSDENIED|在存取資源或功能遭拒時擲回。|
|ChangedStateException|E\_CHANGED\_狀態|在父集合變更後呼叫集合迭代器或集合檢視的方法時擲回，藉以讓該方法的結果失效。|
|ClassNotRegisteredException|REGDB\_E\_CLASSNOTREG|在 COM 類別未登錄時擲回。|
|DisconnectedException|RPC\_E\_已中斷連接|在物件與用戶端的連接中斷時擲回。|
|FailureException|E\_失敗|在作業失敗時擲回。|
|InvalidArgumentException|E\_INVALIDARG|在其中一個提供給方法的引數無效時擲回。|
|InvalidCastException|E\_NOINTERFACE|在類型無法轉換成另一種類型時擲回。|
|NotImplementedException|E\_NOTIMPL|在介面方法未於類別上實作時擲回。|
|NullReferenceException|E\_指標|在嘗試解除 Null 物件的參考時擲回。|
|ObjectDisposedException|RO\_E\_已關閉|在已處置的物件上執行作業時擲回。|
|OperationCanceledException|E\_中止|在作業中止時擲回。|
|OutOfBoundsException|E\_界限|在作業嘗試存取有效範圍以外的資料時擲回。|
|OutOfMemoryException|E\_OUTOFMEMORY|在沒有足夠的記憶體可完成作業時擲回。|
|WrongThreadException|RPC\_E\_錯誤\_執行緒|在執行緒透過不屬於其 Apartment 之 Proxy 物件的介面指標進行呼叫時擲回。|

## <a name="hresult-and-message-properties"></a>HResult 屬性與 Message 屬性

所有例外狀況都有 [HResult](platform-comexception-class.md#hresult) 屬性和 [Message](platform-comexception-class.md#message) 屬性。 [Exception::HResult](platform-exception-class.md#hresult) 屬性會取得例外狀況的基礎數值 HRESULT 值。 [Exception::Message](platform-exception-class.md#message) 屬性會取得系統提供用以說明例外狀況的字串。 在 Windows 8 中，訊息僅適用於偵錯工具，而且是唯讀狀態。 這表示當您重新擲回例外狀況時，無法加以變更。 在 Windows 8.1 中，如果重新擲回例外狀況，可以透過程式設計方式存取訊息字串並提供新的訊息。 偵錯工具中也提供更好的呼叫堆疊資訊，包括非同步方法呼叫的呼叫堆疊。

### <a name="examples"></a>範例

這個範例示範如何擲回同步作業的 Windows 執行階段例外狀況：

[!code-cpp[cx_exceptions#01](codesnippet/CPP/exceptiontest/class1.cpp#01)]

下一個範例說明如何攔截例外狀況。

[!code-cpp[cx_exceptions#02](codesnippet/CPP/exceptiontest/class1.cpp#02)]

若要攔截在非同步作業期間擲回的例外狀況，請使用工作類別並加入錯誤處理接續工作。 錯誤處理接續工作會將其他執行緒上擲回的例外狀況封送回呼叫端執行緒，讓您在程式碼中的單一位置上即可處理所有可能的例外狀況。 如需詳細資訊，請參閱[c + + 進行非同步程式設計](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps)。

## <a name="unhandlederrordetected-event"></a>UnhandledErrorDetected 事件

在 Windows 8.1 中，您可以訂閱以[unhandlederrordetected](/uwp/api/windows.applicationmodel.core.icoreapplicationunhandlederror#Windows_ApplicationModel_Core_ICoreApplicationUnhandledError_UnhandledErrorDetected)靜態事件，以存取即將使處理序的未處理錯誤。 不論錯誤源自何處，到達這個處理常式時為[Windows::ApplicationModel::Core::UnhandledError](/uwp/api/windows.applicationmodel.core.unhandlederror)利用事件引數傳入的物件。 當您針對物件呼叫 `Propagate` 時，它會建立及擲回對應至錯誤代碼類型的 `Platform::*Exception` 。 在 Catch 區塊，您可以視需要儲存使用者狀態，然後透過呼叫 `throw`允許處理序結束，或是執行某個動作，讓程式回到已知狀態。 下列範例示範基本模式：

App.xaml.h： 中

```cpp
void OnUnhandledException(Platform::Object^ sender, Windows::ApplicationModel::Core::UnhandledErrorDetectedEventArgs^ e);
```

App.xaml.cpp： 中

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

C + + /CX 不會使用`finally`子句。

## <a name="see-also"></a>另請參閱

[Visual c + + 語言參考](visual-c-language-reference-c-cx.md)  
[命名空間參考](namespaces-reference-c-cx.md)  
