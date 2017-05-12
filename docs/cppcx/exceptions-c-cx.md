---
title: "例外狀況 (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "01/22/2017"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6cbdc1f1-e4d7-4707-a670-86365146432f
caps.latest.revision: 22
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 22
---
# 例外狀況 (C++/CX)
[!INCLUDE[cppwrt](../cppcx/includes/cppwrt-md.md)] \([!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]\) 中的錯誤處理是以例外狀況為基礎。 在最基本的層次上，[!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]元件會以 HRESULT 值的形式報告錯誤。 在 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 中，這些值會轉換成強類型的例外狀況，其中包含 HRESULT 值和 \(在 [!INCLUDE[win81](../cppcx/includes/win81-md.md)] 中\) 可透過程式設計方式存取的字串描述。  例外狀況會實作為衍生自 `ref class` 的 `Platform::Exception`。`Platform` 命名空間會爲最常見的 HRESULT 值定義不同的例外狀況類別，其他所有的值則透過 `Platform::COMException` 類別來報告。 所有的例外狀況類別都會有可供您擷取原始 HRESULT 的 [Exception::HResult Property](../cppcx/exception-hresult-property.md) 欄位。 在 [!INCLUDE[win81](../cppcx/includes/win81-md.md)] 中，您也可以在偵錯工具中檢查使用者程式碼的呼叫堆疊資訊，協助找出例外狀況的原始來源，即使原始程式碼是以 C\+\+ 以外的語言撰寫。  
  
## 例外狀況  
 在您的 C\+\+ 程式中，您可以擲回並攔截來自 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]作業的例外狀況、衍生自 `std::exception` 的例外狀況或是使用者定義的類型。 只有在 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]例外狀況會跨應用程式二進位介面 \(ABI\) 界限時 \(例如，如果攔截例外狀況的程式碼是以 JavaScript 撰寫的\)，您才需要擲回該例外狀況。 非 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] C\+\+ 例外狀況到達 ABI 界限時，將會轉譯成 `Platform::FailureException` 例外狀況，表示 E\_FAIL HRESULT。 如需 ABI 的詳細資訊，請參閱[在 C\+\+ 中建立 Windows 執行階段元件](http://msdn.microsoft.com/library/5b7251e6-4271-4f13-af80-c1cf5b1489bf)。  
  
 您可以透過採用 HRESULT 參數或採用 HRESULT 參數和 [Platform::String](../cppcx/platform-exception-class.md)^ 參數的兩個建構函式之一，來宣告可跨 ABI 傳遞至任何處理例外狀況的 Windows 市集應用程式的 [Platform::Exception](../cppcx/platform-string-class.md)。 或者，您可以透過採用 HRESULT 參數或採用 HRESULT 參數和 `Platform::String^` 參數的兩個 [Exception::CreateException 方法](../cppcx/exception-createexception-method.md)多載之一，來宣告例外狀況。  
  
## 標準例外狀況  
 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 支援一組代表一般 HRESULT 錯誤的標準例外狀況。 每個標準例外狀況皆衍生自 [Platform::COMException](../cppcx/platform-comexception-class.md)，而後者又衍生自 `Platform::Exception`。 當您擲回跨 ABI 界限的例外狀況時，您必須擲回其中一個標準例外狀況。  
  
 您無法從 `Platform::Exception` 衍生您自己的例外狀況型別。 若要擲回自訂例外狀況，請透過使用者定義的 HRESULT 來建構 `COMException` 物件。  
  
 下表列出標準例外狀況。  
  
|名稱|基礎 HRESULT|描述|  
|--------|----------------|--------|  
|COMException|*使用者定義的 HRESULT*|在 COM 方法呼叫傳回無法辨認的 HRESULT 時擲回。|  
|AccessDeniedException|E\_ACCESSDENIED|在存取資源或功能遭拒時擲回。|  
|ChangedStateException|E\_CHANGED\_STATE|在父集合變更後呼叫集合迭代器或集合檢視的方法時擲回，藉以讓該方法的結果失效。|  
|ClassNotRegisteredException|REGDB\_E\_CLASSNOTREG|在 COM 類別未登錄時擲回。|  
|DisconnectedException|RPC\_E\_DISCONNECTED|在物件與用戶端的連接中斷時擲回。|  
|FailureException|E\_FAIL|在作業失敗時擲回。|  
|InvalidArgumentException|E\_INVALIDARG|在其中一個提供給方法的引數無效時擲回。|  
|InvalidCastException|E\_NOINTERFACE|在類型無法轉換成另一種類型時擲回。|  
|NotImplementedException|E\_NOTIMPL|在介面方法未於類別上實作時擲回。|  
|NullReferenceException|E\_POINTER|在嘗試解除 Null 物件的參考時擲回。|  
|ObjectDisposedException|RO\_E\_CLOSED|在已處置的物件上執行作業時擲回。|  
|OperationCanceledException|E\_ABORT|在作業中止時擲回。|  
|OutOfBoundsException|E\_BOUNDS|在作業嘗試存取有效範圍以外的資料時擲回。|  
|OutOfMemoryException|E\_OUTOFMEMORY|在沒有足夠的記憶體可完成作業時擲回。|  
|WrongThreadException|RPC\_E\_WRONG\_THREAD|在執行緒透過不屬於其 Apartment 之 Proxy 物件的介面指標進行呼叫時擲回。|  
  
## HResult 屬性與 Message 屬性  
 所有例外狀況都有 [HResult](../cppcx/comexception-hresult-property.md) 屬性和 [Message](../cppcx/comexception-message-property.md) 屬性。[Exception::HResult](../cppcx/exception-hresult-property.md) 屬性會取得例外狀況的基礎數值 HRESULT 值。[Exception::Message](../cppcx/exception-message-property.md) 屬性會取得系統提供用以說明例外狀況的字串。 在 [!INCLUDE[win8](../cppcx/includes/win8-md.md)] 中，訊息只出現在偵錯工具中，而且是唯讀的。 這表示當您重新擲回例外狀況時，無法加以變更。 在 [!INCLUDE[win81](../cppcx/includes/win81-md.md)] 中，如果重新擲回例外狀況，可以透過程式設計方式存取訊息字串並提供新的訊息。 偵錯工具中也提供更好的呼叫堆疊資訊，包括非同步方法呼叫的呼叫堆疊。  
  
## 範例  
 此範例說明如何擲回同步作業的 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]例外狀況：  
  
 [!code-cpp[cx_exceptions#01](../snippets/cpp/VS_Snippets_Misc/cx_exceptions/cpp/class1.cpp#01)]  
  
 下一個範例說明如何攔截例外狀況。  
  
 [!code-cpp[cx_exceptions#02](../snippets/cpp/VS_Snippets_Misc/cx_exceptions/cpp/class1.cpp#02)]  
  
 若要攔截在非同步作業期間擲回的例外狀況，請使用工作類別並加入錯誤處理接續工作。 錯誤處理接續工作會將其他執行緒上擲回的例外狀況封送回呼叫端執行緒，讓您在程式碼中的單一位置上即可處理所有可能的例外狀況。 如需詳細資訊，請參閱[使用 C\+\+ 進行非同步程式設計](http://msdn.microsoft.com/library/windows/apps/Hh780559.aspx)。  
  
## UnhandledErrorDetected 事件  
 在 [!INCLUDE[win81](../cppcx/includes/win81-md.md)] 中，可訂閱 [Windows::ApplicationModel::Core::CoreApplication::UnhandledErrorDetected](http://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.coreapplication.unhandlederrordetected.aspx) 靜態事件，以存取即將使處理序失敗的未處理錯誤。 不論錯誤源自何處，它都會以透過事件引數傳入的 [Windows::ApplicationModel::Core::UnhandledError](http://msdnstage.redmond.corp.microsoft.com/library/windows/apps/windows.applicationmodel.core.unhandlederror.aspx) 物件形式，到達這個處理常式。 當您針對物件呼叫 `Propagate` 時，它會建立及擲回對應至錯誤代碼類型的 `Platform::*Exception`。 在 Catch 區塊，您可以視需要儲存使用者狀態，然後透過呼叫 `throw` 允許處理序結束，或是執行某個動作，讓程式回到已知狀態。 下列範例示範基本模式：  
  
```  
  
// In app.xaml.h:  
void OnUnhandledException(Platform::Object^ sender, Windows::ApplicationModel::Core::UnhandledErrorDetectedEventArgs^ e);  
  
// In app.xaml.cpp  
  
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
  
## 備註  
 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 不會使用 `finally` 子句。  
  
## 請參閱  
 [Visual C\+\+ 語言參考](../cppcx/visual-c-language-reference-c-cx.md)   
 [命名空間參考](../cppcx/namespaces-reference-c-cx.md)