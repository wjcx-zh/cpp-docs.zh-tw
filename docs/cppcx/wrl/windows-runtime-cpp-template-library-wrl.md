---
title: Windows Runtime C++ Template Library (WRL)
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: b915afce-553b-44a7-b8dc-0ab601758eb0
ms.openlocfilehash: 5c1a4e7df424499f400dbd70d675956deef6bc5d
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58784351"
---
# <a name="windows-runtime-c-template-library-wrl"></a>Windows Runtime C++ Template Library (WRL)

Windows 執行階段 C++ 範本庫 (WRL) 是提供低階方式撰寫和使用 Windows 執行階段元件的範本庫。

> [!NOTE]
> WRL 現在已取代C++/WinRT、 標準 C + + 17 語言推演，適用於 Windows 執行階段 Api。 C++/ 在 Windows 10 SDK 版本 1803年之後推出 WinRT。 C++/ WinRT 是完全在標頭檔中實作，並設計為您提供第一級存取新式 Windows api。
>
> 使用C++/WinRT，您可以使用及撰寫 Windows 執行階段 Api 使用任何符合標準的 C + + 17 編譯器。 C++/ WinRT 通常會執行得更好，並產生較小的二進位檔，比 Windows 執行階段的其他語言選項。 我們會繼續支援C++/CX 和 WRL，但強烈建議使用新的應用程式C++/WinRT。 如需詳細資訊，請參閱 < [ C++/WinRT](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/index)。

## <a name="benefits"></a>優點

Windows 執行階段C++範本程式庫可讓您更輕鬆地實作和使用元件物件模型 (COM) 元件。 它提供環境維護技術，例如參考計數來管理物件的存留期和測試以判斷作業是否成功或失敗的 HRESULT 值。 若要順利使用 Windows 執行階段C++樣板程式庫，您必須小心遵循這些規則和技術。

C++/CX 是使用 Windows 執行階段元件的高階、 以語言為基礎的方法。 這兩個 Windows 執行階段C++樣板程式庫和C++/CX 來簡化撰寫程式碼適用於 Windows 執行階段會自動代替您執行環境維護工作。

Windows 執行階段C++樣板程式庫和C++/CX 提供不同的優點。 以下是一些您可能想要使用 Windows 執行階段的原因C++樣板程式庫，而不是C++/CX:

- Windows 執行階段C++樣板程式庫沒有加入透過 Windows 執行階段應用程式二進位介面 (ABI)，讓您能夠控制基礎的程式碼，更有效建立或使用 Windows 執行階段 Api。

- C++/CX 當做例外狀況代表 COM HRESULT 值。 如果您繼承了使用 COM 或沒有使用例外狀況的程式碼基底，您可能會發現 Windows 執行階段C++範本程式庫是以更自然的方式來使用 Windows 執行階段，因為您不需要使用例外狀況。

   > [!NOTE]
   > Windows 執行階段C++樣板程式庫會使用 HRESULT 值，並不會擲回例外狀況。 此外，Windows 執行階段C++樣板程式庫會使用智慧型指標和 RAII 模式，協助確保您的應用程式程式碼擲回例外狀況時物件會正確地終結。 如需智慧型指標和 RAII 的詳細資訊，請參閱[智慧型指標](../../cpp/smart-pointers-modern-cpp.md)並[物件自己的資源 (RAII)](../../cpp/objects-own-resources-raii.md)。

- 用途和設計的 Windows 執行階段C++樣板程式庫啟發的 Active Template Library (ATL)，也就是一組範本為基礎的C++類別來簡化 COM 物件的程式設計。 因為 Windows 執行階段C++範本程式庫會使用標準C++來包裝 Windows 執行階段，您可以更輕鬆地連接埠並與其互動以 ATL 撰寫 Windows 執行階段的許多現有 COM 元件。 如果您已經知道 ATL，您可能會發現該 Windows 執行階段C++範本庫程式設計會更為容易。

## <a name="getting-started"></a>快速入門

以下是一些可協助您開始使用 Windows 執行階段的資源C++立即樣板程式庫。

[Windows 執行階段程式庫 (WRL)](https://channel9.msdn.com/Events/Windows-Camp/Developing-Windows-8-Metro-style-apps-in-Cpp/The-Windows-Runtime-Library-WRL-)<br/>
在這個 Channel 9 影片中，進一步了解 Windows 執行階段C++樣板程式庫可協助您撰寫通用 Windows 平台 (UWP) 應用程式，以及如何撰寫和使用 Windows 執行階段元件。

[如何：啟動與使用 Windows 執行階段元件](how-to-activate-and-use-a-windows-runtime-component-using-wrl.md)<br/>
示範如何使用 Windows 執行階段C++來初始化 Windows 執行階段以及啟用和使用 Windows 執行階段元件的範本庫。

[如何：完成非同步作業](how-to-complete-asynchronous-operations-using-wrl.md)<br/>
示範如何使用 Windows 執行階段C++來啟動非同步作業，並在作業完成時執行工作的範本程式庫。

[如何：處理事件](how-to-handle-events-using-wrl.md)<br/>
示範如何使用 Windows 執行階段C++訂閱，以及處理事件的 Windows 執行階段物件的範本程式庫。

[逐步解說：使用 WRL 與媒體基礎建立 UWP 應用程式](walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation.md)<br/>
了解如何建立使用 UWP 應用程式[Microsoft 媒體基礎](/windows/desktop/medfound/microsoft-media-foundation-sdk)。

[如何：建立傳統 COM 元件](how-to-create-a-classic-com-component-using-wrl.md)<br/>
示範如何使用 Windows 執行階段C++來建立基本的 COM 元件和基本的方式來註冊和使用桌面應用程式的 COM 元件的範本庫。

[如何：直接執行個體化 WRL 元件](how-to-instantiate-wrl-components-directly.md)<br/>
了解如何使用 [Microsoft::WRL::Make](make-function.md) 和 [Microsoft::WRL::Details::MakeAndInitialize](makeandinitialize-function.md) 函式，從定義元件的模組中具現化元件。

[如何：使用 winmdidl.exe 和 midlrt.exe 根據 Windows 中繼資料建立 .h 檔案](use-winmdidl-and-midlrt-to-create-h-files-from-windows-metadata.md)<br/>
顯示如何透過從 .winmd 中繼資料建立 IDL 檔案，使用 WRL 的自訂 Windows 執行階段元件。

[逐步解說：使用工作和 XML HTTP 要求進行連線](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)<br/>
示範如何使用[IXMLHTTPRequest2](/windows/desktop/api/msxml6/nn-msxml6-ixmlhttprequest2)並[IXMLHTTPRequest2Callback](/windows/desktop/api/msxml6/nn-msxml6-ixmlhttprequest2callback)介面，以及將 HTTP GET 和 POST 要求傳送至 UWP 應用程式中的 web 服務的工作。

[Bing 地圖服務路線最佳化程式範例](https://code.msdn.microsoft.com/Bing-Maps-trip-optimizer-c4e037f7)<br/>
會使用`HttpRequest`中所定義的類別[逐步解說：使用工作和 XML HTTP 要求連線](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)完成的 UWP 應用程式的內容中。

[建立 Windows 執行階段 DLL 元件與C++範例](https://code.msdn.microsoft.com/windowsapps/Creating-a-Windows-Runtime-6c399797)<br/>
示範如何使用 Windows 執行階段C++若要建立同處理序 DLL 元件，然後使用它從樣板程式庫C++/CX、 JavaScript 和C#。

[DirectX 彈珠迷宮遊戲範例](https://code.msdn.microsoft.com/windowsapps/DirectX-Marble-Maze-Game-e4806345)<br/>
示範如何使用 Windows 執行階段C++範本程式庫來管理在完整 3d 遊戲的內容中，如 DirectX 和媒體基礎 COM 元件的存留期。

[從桌面應用程式範例傳送快顯通知](https://code.msdn.microsoft.com/windowsdesktop/Sending-toast-notifications-71e230a2)<br/>
示範如何使用 Windows 執行階段C++來處理從傳統型應用程式的快顯通知的範本程式庫。

## <a name="windows-runtime-c-template-library-compared-to-atl"></a>Windows 執行階段C++樣板程式庫和 ATL 比較

Windows 執行階段C++樣板程式庫類似 Active Template Library (ATL)，因為您可以使用它來建立小型、 快速的 COM 物件。 Windows 執行階段C++樣板程式庫和 ATL 也共用概念，例如在模組中，明確註冊介面，物件的定義，以及使用 factory 開放式建立物件。 您可能熟悉 Windows 執行階段C++如果您熟悉 ATL 的範本程式庫

Windows 執行階段C++範本程式庫支援的 UWP 應用程式的 COM 功能。 因此，它與 ATL 不同，因為後者省略直接支援 COM 功能，例如：

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

Windows 執行階段C++範本程式庫提供代表某些基本概念的類型。 下列章節將說明這些類型：

### <a name="comptr"></a>ComPtr

[ComPtr](comptr-class.md) 是 *智慧型指標* 類型，表示由範本參數指定之介面。 使用 `ComPtr` 來宣告變數，以存取從介面衍生之物件的成員。 `ComPtr` 自動維護基礎介面指標的參考計數，並在參考計數歸零時釋放介面。

### <a name="runtimeclass"></a>RuntimeClass

[RuntimeClass](runtimeclass-class.md) 表示繼承一組指定之介面的具現化類別。 A`RuntimeClass`物件可以提供一或多個 Windows 執行階段的 COM 介面或元件的弱式參考支援的組合。

### <a name="module"></a>Module

[Module](module-class.md) 表示相關物件的集合。 `Module` 物件管理 Class Factory 和註冊，前者會建立物件，後者讓其他應用程式使用物件。

### <a name="callback"></a>回呼

[Callback](callback-function-wrl.md) 函式建立成員函式是事件處理常式的物件 (回呼方法)。 使用 `Callback` 函式撰寫非同步作業。

### <a name="eventsource"></a>EventSource

[EventSource](eventsource-class.md) 用來管理「 *委派* 」(Delegate) 事件處理常式。 使用 Windows 執行階段C++實作委派，並使用範本庫`EventSource`新增、 移除及叫用委派。

### <a name="asyncbase"></a>AsyncBase

[AsyncBase](asyncbase-class.md)提供代表 Windows 執行階段非同步程式設計模型的虛擬方法。 覆寫這個類別中的成員，建立可以啟動、停止或檢查非同步作業進度的自訂類別。

### <a name="ftmbase"></a>FtmBase

[FtmBase](ftmbase-class.md) 代表無限制執行緒封送處理器物件。 `FtmBase` 建立全域介面表 (GIT)，並協助管理封送處理和 Proxy 物件。

### <a name="weakref"></a>WeakRef

[WeakRef](weakref-class.md) 是代表 *弱式參考*的智慧型指標類型，會參考不一定可存取的物件。 A`WeakRef`物件可以用，只有在 Windows 執行階段，而不是傳統 com 使用。

`WeakRef` 物件通常代表其存在是由外部執行緒或應用程式所控制的物件。 例如， `WeakRef` 物件可以參考檔案物件。 在檔案開啟時， `WeakRef` 有效，而且參考的檔案是可存取的。 不過，在檔案關閉時， `WeakRef` 是無效，而且檔案無法存取。

## <a name="related-topics"></a>相關主題

|||
|-|-|
|[依類別目錄的索引鍵 Api](key-wrl-apis-by-category.md)|主要的 Windows 執行階段會反白顯示C++樣板程式庫類型、 函數和巨集。|
|[參考資料](wrl-reference.md)|包含 Windows 執行階段的參考資訊C++樣板程式庫。|
|[快速參考 (Windows 執行階段和視覺效果C++)](../../cppcx/quick-reference-c-cx.md)|簡短描述C++/CX 功能，可支援 Windows 執行階段。|
|[在 視覺效果中使用 Windows 執行階段元件C++](/windows/uwp/winrt-components/walkthrough-creating-a-basic-windows-runtime-component-in-cpp-and-calling-it-from-javascript-or-csharp)|示範如何使用C++/CX 建立基本 Windows 執行階段元件。|
