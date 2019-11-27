---
title: Windows Runtime C++ Template Library (WRL)
ms.date: 11/04/2016
ms.topic: overview
ms.assetid: b915afce-553b-44a7-b8dc-0ab601758eb0
ms.openlocfilehash: 7a7b37a32ebaa0bb6ad71c8f710300256589388d
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541196"
---
# <a name="windows-runtime-c-template-library-wrl"></a>Windows Runtime C++ Template Library (WRL)

Windows 執行階段 C++ 範本庫 (WRL) 是提供低階方式撰寫和使用 Windows 執行階段元件的範本庫。

> [!NOTE]
> WRL 現在已由C++/WinRT 取代，這是適用于 Windows 執行階段 api 的 Standard c + + 17 語言投影。 C++從1803版開始，Windows 10 SDK 中提供了/WinRT。 C++/WinRT 會完全實作為標頭檔，並設計來提供您對新式 Windows API 的第一級存取。
>
> 透過C++/WinRT，您可以使用任何符合標準的 c + + 17 編譯器來取用和撰寫 Windows 執行階段 api。 C++/WinRT 通常會執行得更好，而且會產生比 Windows 執行階段的任何其他語言選項更小的二進位檔。 我們將繼續支援 C++/CX 和 WRL，但強烈建議讓新的應用程式使用 C++/WinRT。 如需詳細資訊，請參閱 [C++/WinRT](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/index)。

## <a name="benefits"></a>優點

Windows 執行階段C++範本庫可讓您更輕鬆地執行和取用元件物件模型（COM）元件。 它提供了維護技術（例如參考計數）來管理物件的存留期，以及測試 HRESULT 值來判斷作業是否成功或失敗。 若要成功使用 Windows 執行階段C++的範本庫，您必須仔細遵循這些規則和技術。

C++/Cx 是使用 Windows 執行階段元件的高階、以語言為基礎的方式。 Windows 執行階段C++範本庫和C++/cx 皆會自動代表您執行維護工作，以簡化 Windows 執行階段的程式碼撰寫作業。

Windows 執行階段C++範本庫和C++/cx 提供不同的優點。 以下是您可能想要使用 Windows 執行階段C++範本庫，而不是/cx C++的一些原因：

- Windows 執行階段C++範本程式庫在 Windows 執行階段的應用程式二進位介面（ABI）上加入了一些抽象概念，讓您能夠控制基礎程式碼，以更好的建立或使用 Windows 執行階段 api。

- C++/CX 代表 COM HRESULT 值做為例外狀況。 如果您繼承了使用 COM 的程式碼基底，或是不使用例外狀況的程式碼，您可能會C++發現 Windows 執行階段範本庫是使用 Windows 執行階段的更自然方式，因為您不需要使用例外狀況。

   > [!NOTE]
   > Windows 執行階段C++範本庫會使用 HRESULT 值，而且不會擲回例外狀況。 此外，Windows 執行階段C++範本庫也會使用智慧型指標和 RAII 模式，協助確保當應用程式代碼擲回例外狀況時，物件會正確地終結。 如需智慧型指標和 RAII 的詳細資訊，請參閱[智慧型指標](../../cpp/smart-pointers-modern-cpp.md)和[物件擁有資源（RAII）](../../cpp/objects-own-resources-raii.md)。

- Windows 執行階段C++範本庫的目的和設計是由 ACTIVE TEMPLATE LIBRARY （ATL）所啟發，這是一組以範本為基礎C++的類別，可簡化 COM 物件的程式設計。 因為 Windows 執行階段C++範本庫使用標準C++來包裝 Windows 執行階段，所以您可以更輕鬆地將許多以 ATL 撰寫的現有 COM 元件移植到 Windows 執行階段，並與之互動。 如果您已經知道 ATL，您可能會發現 Windows 執行階段C++範本庫程式設計變得更容易。

## <a name="getting-started"></a>使用者入門

以下是一些可協助您立即使用 Windows 執行階段C++範本庫的資源。

[Windows 執行階段程式庫（WRL）](https://channel9.msdn.com/Events/Windows-Camp/Developing-Windows-8-Metro-style-apps-in-Cpp/The-Windows-Runtime-Library-WRL-)<br/>
在此 Channel 9 影片中，深入瞭解 Windows 執行階段C++範本庫如何協助您撰寫通用 WINDOWS 平臺（UWP）應用程式，以及如何撰寫和使用 Windows 執行階段元件。

[如何：啟動和使用 Windows 執行階段元件](how-to-activate-and-use-a-windows-runtime-component-using-wrl.md)<br/>
示範如何使用 Windows 執行階段C++範本庫來初始化 Windows 執行階段並啟用和使用 Windows 執行階段元件。

[如何：完成非同步作業](how-to-complete-asynchronous-operations-using-wrl.md)<br/>
示範如何使用 Windows 執行階段C++範本庫來啟動非同步作業，並在作業完成時執行工作。

[如何：處理事件](how-to-handle-events-using-wrl.md)<br/>
示範如何使用 Windows 執行階段C++範本庫來訂閱和處理 Windows 執行階段物件的事件。

[逐步解說： 使用 WRL 與媒體基礎建立 UWP 應用程式](walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation.md)<br/>
瞭解如何建立使用[Microsoft 媒體基礎](/windows/win32/medfound/microsoft-media-foundation-sdk)的 UWP 應用程式。

[如何：建立傳統 COM 元件](how-to-create-a-classic-com-component-using-wrl.md)<br/>
示範如何使用 Windows 執行階段C++範本程式庫來建立基本的 com 元件，以及從桌面應用程式註冊和取用 COM 元件的基本方法。

[如何：直接具現化 WRL 元件](how-to-instantiate-wrl-components-directly.md)<br/>
了解如何使用 [Microsoft::WRL::Make](make-function.md) 和 [Microsoft::WRL::Details::MakeAndInitialize](makeandinitialize-function.md) 函式，從定義元件的模組中具現化元件。

[如何：使用 winmdidl.exe 和 midlrt.exe 根據 Windows 中繼資料建立 .h 檔案](use-winmdidl-and-midlrt-to-create-h-files-from-windows-metadata.md)<br/>
顯示如何透過從 .winmd 中繼資料建立 IDL 檔案，使用 WRL 的自訂 Windows 執行階段元件。

[逐步解說：使用工作和 XML HTTP 要求連接](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)<br/>
說明如何搭配使用[IXMLHTTPRequest2](/windows/win32/api/msxml6/nn-msxml6-ixmlhttprequest2)和[IXMLHTTPRequest2Callback](/windows/win32/api/msxml6/nn-msxml6-ixmlhttprequest2callback)介面與工作，將 HTTP GET 和 POST 要求傳送至 UWP 應用程式中的 web 服務。

[Bing 地圖服務路線優化程式範例](https://code.msdn.microsoft.com/Bing-Maps-trip-optimizer-c4e037f7)<br/>
使用在[逐步解說：使用工作和 XML HTTP 要求](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)在完整 UWP 應用程式的內容中進行連接中定義的 `HttpRequest` 類別。

[使用C++範例建立 Windows 執行階段 DLL 元件](https://code.msdn.microsoft.com/windowsapps/Creating-a-Windows-Runtime-6c399797)<br/>
示範如何使用 Windows 執行階段C++範本庫來建立同進程 DLL 元件，並從C++/cx、JavaScript 和C#取用它。

[DirectX 大理石迷宮遊戲範例](https://docs.microsoft.com/samples/microsoft/windows-appsample-marble-maze/directx-marble-maze-game-sample/)<br/>
示範如何使用 Windows 執行階段C++的範本程式庫，在完整的3-d 遊戲內容中管理 COM 元件（例如 DirectX 和媒體基礎）的存留期。

[從桌面應用程式傳送快顯通知範例](https://code.msdn.microsoft.com/windowsdesktop/Sending-toast-notifications-71e230a2)<br/>
示範如何使用 Windows 執行階段C++範本庫，從桌面應用程式處理快顯通知。

## <a name="windows-runtime-c-template-library-compared-to-atl"></a>相C++較于 ATL，Windows 執行階段範本庫

Windows 執行階段C++範本庫類似于 ACTIVE TEMPLATE LIBRARY （ATL），因為您可以用它來建立小型、快速的 COM 物件。 Windows 執行階段C++樣板程式庫和 ATL 也會共用概念，例如在模組中定義物件、明確註冊介面，以及使用 factory 來開啟物件的建立。 如果您熟悉 ATL，您C++可能會習慣 Windows 執行階段的範本庫。

Windows 執行階段C++範本庫支援 UWP 應用程式所需的 COM 功能。 因此，它與 ATL 不同，因為後者省略直接支援 COM 功能，例如：

- 彙總

- 內建實作

- 雙重介面 (`IDispatch`)

- 標準列舉程式介面

- 連接點

- Tear-Off 介面

- OLE 內嵌

- ActiveX 控制項

- COM+

## <a name="concepts"></a>概念

Windows 執行階段C++範本庫提供代表一些基本概念的類型。 下列章節將說明這些類型：

### <a name="comptr"></a>ComPtr

[ComPtr](comptr-class.md) 是 *智慧型指標* 類型，表示由範本參數指定之介面。 使用 `ComPtr` 來宣告變數，以存取從介面衍生之物件的成員。 `ComPtr` 自動維護基礎介面指標的參考計數，並在參考計數歸零時釋放介面。

### <a name="runtimeclass"></a>RuntimeClass

[RuntimeClass](runtimeclass-class.md) 表示繼承一組指定之介面的具現化類別。 `RuntimeClass` 物件可以提供一或多個 Windows 執行階段 COM 介面的支援組合，或元件的弱式參考。

### <a name="module"></a>Module

[Module](module-class.md) 表示相關物件的集合。 `Module` 物件管理 Class Factory 和註冊，前者會建立物件，後者讓其他應用程式使用物件。

### <a name="callback"></a>回呼

[Callback](callback-function-wrl.md) 函式建立成員函式是事件處理常式的物件 (回呼方法)。 使用 `Callback` 函式撰寫非同步作業。

### <a name="eventsource"></a>EventSource

[EventSource](eventsource-class.md) 用來管理「 *委派* 」(Delegate) 事件處理常式。 使用 Windows 執行階段C++範本庫來執行委派，並使用 `EventSource` 來新增、移除及叫用委派。

### <a name="asyncbase"></a>AsyncBase

[AsyncBase](asyncbase-class.md)提供代表 Windows 執行階段非同步程式設計模型的虛擬方法。 覆寫這個類別中的成員，建立可以啟動、停止或檢查非同步作業進度的自訂類別。

### <a name="ftmbase"></a>FtmBase

[FtmBase](ftmbase-class.md) 代表無限制執行緒封送處理器物件。 `FtmBase` 建立全域介面表 (GIT)，並協助管理封送處理和 Proxy 物件。

### <a name="weakref"></a>WeakRef

[WeakRef](weakref-class.md) 是代表 *弱式參考*的智慧型指標類型，會參考不一定可存取的物件。 `WeakRef` 的物件只能由 Windows 執行階段使用，而不能由傳統 COM 使用。

`WeakRef` 物件通常代表其存在是由外部執行緒或應用程式所控制的物件。 例如， `WeakRef` 物件可以參考檔案物件。 在檔案開啟時， `WeakRef` 有效，而且參考的檔案是可存取的。 不過，在檔案關閉時， `WeakRef` 是無效，而且檔案無法存取。

## <a name="related-topics"></a>相關主題

|||
|-|-|
|[依類別分類的主要 Api](key-wrl-apis-by-category.md)|反白顯示主要C++ Windows 執行階段範本程式庫類型、函式和宏。|
|[參考資料](wrl-reference.md)|包含 Windows 執行階段C++範本程式庫的參考資訊。|
|[快速參考C++/cx）](../../cppcx/quick-reference-c-cx.md)|簡要描述支援C++Windows 執行階段的/cx 功能。|
|[在視覺效果中使用 Windows 執行階段元件C++](/windows/uwp/winrt-components/walkthrough-creating-a-basic-windows-runtime-component-in-cpp-and-calling-it-from-javascript-or-csharp)|示範如何使用C++/cx 來建立基本 Windows 執行階段元件。|
