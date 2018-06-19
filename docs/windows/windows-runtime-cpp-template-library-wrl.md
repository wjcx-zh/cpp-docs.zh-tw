---
title: Windows 執行階段 c + + 樣板程式庫 (WRL) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: b915afce-553b-44a7-b8dc-0ab601758eb0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 40d2ecbcfcd4121727bfe34bf2ffd571722b8a68
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891619"
---
# <a name="windows-runtime-c-template-library-wrl"></a>Windows Runtime C++ Template Library (WRL)
Windows 執行階段 C++ 範本庫 (WRL) 是提供低階方式撰寫和使用 Windows 執行階段元件的範本庫。

> [!NOTE]
> WRL 現在取代 C + WinRT，standard C + + 17 語言投影適用於 Windows 執行階段 Api。 C + + WinRT 適用於 Windows 10 SDK 版本 1803年開始。 C + + WinRT 是完全在標頭檔中實作及設計來提供您具有第一級的存取權的現代 Windows api。

> 使用 C + + WinRT，您可以使用及撰寫 Windows 執行階段 Api 使用任何符合標準的 C + + 17 編譯器。 C + + WinRT 通常更好，而且會產生較小的二進位檔，比為 Windows 執行階段的其他語言選項。 我們將繼續支援 C + + /CX 和 WRL，但強烈建議您，新的應用程式使用 C + + WinRT。 如需詳細資訊，請參閱[C + + WinRT](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/index)。   
  
## <a name="benefits"></a>優點  
 Windows 執行階段 c + + 樣板程式庫可讓您更輕鬆地實作和使用元件物件模型 (COM) 元件。 它提供環境維護技術，如參考計數來管理物件的存留期，以及測試 `HRESULT` 值來判斷作業成功或失敗。 若要順利使用 Windows 執行階段 c + + 樣板程式庫，您必須小心遵循這些規則和技術。  
  
 C + + /CX 是使用 Windows 執行階段元件的高階、 以語言為基礎的方法。 Windows 執行階段 c + + 樣板程式庫和 C + + /CX 簡化程式碼撰寫為 Windows 執行階段透過自動代表您執行環境維護工作。  
  
 Windows 執行階段 c + + 樣板程式庫和 C + + /CX 提供不同的優點。 以下是一些原因，您可能想要使用 Windows 執行階段 c + + 樣板程式庫，而不是 C + + /CX:  
  
-   Windows 執行階段 c + + 樣板程式庫加入一些太多抽象性透過 Windows 執行階段應用程式二進位介面 (ABI)，讓您可以控制基礎程式碼，以更好地建立或使用 Windows 執行階段 Api。  
  
-   C + + /CX 代表 COM`HRESULT`當做例外狀況的值。 如果您繼承了使用 COM 或沒有使用例外狀況的程式碼基底，您可能會發現 Windows 執行階段 c + + 樣板程式庫是更自然的方式來使用 Windows 執行階段，因為您沒有使用例外狀況。  
  
    > [!NOTE]
    >  Windows 執行階段 c + + 樣板程式庫會使用`HRESULT`值並不會擲回例外狀況。 此外，Windows 執行階段 c + + 樣板程式庫會使用智慧型指標和 RAII 模式來協助您的應用程式程式碼擲回例外狀況時物件被正確地終結。 如需智慧型指標和 RAII 的詳細資訊，請參閱[智慧型指標](../cpp/smart-pointers-modern-cpp.md)和[物件自己的資源 (RAII)](../cpp/objects-own-resources-raii.md)。  
  
-   用途和設計的 Windows 執行階段 c + + 樣板程式庫被啟發由 Active Template Library (ATL)，這是一組樣板架構 c + + 類別，可簡化 COM 物件程式設計。 因為 Windows 執行階段 c + + 樣板程式庫會使用標準 c + + 包裝 Windows 執行階段，您就可以更輕鬆地連接埠，並與 Windows 執行階段以 ATL 撰寫的許多現有 COM 元件互動。 如果您已經知道 ATL，您可能會發現 Windows 執行階段 c + + 樣板程式庫程式設計會更為容易。  
  
## <a name="getting-started"></a>快速入門  
 以下是一些資源可協助您開始使用 Windows 執行階段 c + + 樣板程式庫以立即開始。  
  
 [Windows 執行階段程式庫 (WRL)](http://channel9.msdn.com/Events/Windows-Camp/Developing-Windows-8-Metro-style-apps-in-Cpp/The-Windows-Runtime-Library-WRL-)  
 在這個 Channel 9 影片，進一步了解 Windows 執行階段 c + + 樣板程式庫如何協助您撰寫的通用 Windows 平台 (UWP) 應用程式，以及如何撰寫和使用 Windows 執行階段元件。  
  
 [如何： 啟用和使用 Windows 執行階段元件](../windows/how-to-activate-and-use-a-windows-runtime-component-using-wrl.md)  
 示範如何使用 Windows 執行階段 c + + 樣板程式庫初始化 Windows 執行階段以及啟用和使用 Windows 執行階段元件。  
  
 [如何： 完成非同步作業](../windows/how-to-complete-asynchronous-operations-using-wrl.md)  
 示範如何使用 Windows 執行階段 c + + 樣板程式庫，若要啟動非同步作業和作業完成時執行工作。  
  
 [如何： 處理事件](../windows/how-to-handle-events-using-wrl.md)  
 示範如何使用 Windows 執行階段 c + + 樣板程式庫訂閱和處理 Windows 執行階段物件的事件。  
  
 [逐步解說： 使用 WRL 與媒體基礎建立 UWP 應用程式](../windows/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation.md)  
 了解如何建立 UWP 應用程式使用[Microsoft 媒體基礎](http://msdn.microsoft.com/library/windows/apps/ms694197)。  
  
 [如何： 建立傳統 COM 元件](../windows/how-to-create-a-classic-com-component-using-wrl.md)  
 示範如何使用 Windows 執行階段 c + + 樣板程式庫來建立基本的 COM 元件，以及註冊和使用桌面應用程式的 COM 元件的基本方法。  
  
 [如何：直接具現化 WRL 元件](../windows/how-to-instantiate-wrl-components-directly.md)  
 了解如何使用[Microsoft::WRL::Make](../windows/make-function.md)和[Microsoft::WRL::Details::MakeAndInitialize](../windows/makeandinitialize-function.md)函式來具現化元件，以從模組中定義。  
  
 [如何：使用 winmdidl.exe 和 midlrt.exe 根據 Windows 中繼資料建立 .h 檔案](../windows/use-winmdidl-and-midlrt-to-create-h-files-from-windows-metadata.md)  
 顯示如何透過從 .winmd 中繼資料建立 IDL 檔案，使用 WRL 的自訂 Windows 執行階段元件。  
  
 [逐步解說：使用工作和 XML HTTP 要求連接](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)  
 示範如何使用[IXMLHTTPRequest2](http://msdn.microsoft.com/en-us/bbc11c4a-aecf-4d6d-8275-3e852e309908)和[IXMLHTTPRequest2Callback](http://msdn.microsoft.com/en-us/aa4b3f4c-6e28-458b-be25-6cce8865fc71)介面，以及將 HTTP GET 和 POST 要求傳送至 UWP 應用程式中的 web 服務工作。  
  
 [Bing 地圖服務路線最佳化程式範例](http://code.msdn.microsoft.com/Bing-Maps-trip-optimizer-c4e037f7)  
 使用`HttpRequest`中定義的類別[逐步解說： 使用工作和 XML HTTP 要求](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)完整的 UWP 應用程式的內容中。  
  
 [使用 c + + 範例建立 Windows 執行階段 DLL 元件](http://code.msdn.microsoft.com/windowsapps/Creating-a-Windows-Runtime-6c399797)  
 示範如何使用 Windows 執行階段 c + + 樣板程式庫，若要建立同處理序 DLL 元件，然後使用它從 C + + /CX、 JavaScript 和 C#。  
  
 [DirectX 彈珠迷宮遊戲範例](http://code.msdn.microsoft.com/windowsapps/DirectX-Marble-Maze-Game-e4806345)  
 示範如何使用 Windows 執行階段 c + + 樣板程式庫管理在完整 3d 遊戲的內容中，如 DirectX 和媒體基礎 COM 元件的存留期。  
  
 [從桌面應用程式範例傳送快顯通知](http://code.msdn.microsoft.com/windowsdesktop/Sending-toast-notifications-71e230a2)  
 示範如何使用 Windows 執行階段 c + + 樣板程式庫來處理來自桌面應用程式快顯通知。  
  
## <a name="windows-runtime-c-template-library-compared-to-atl"></a>Windows 執行階段 c + + 樣板程式庫和 ATL 比較  
 Windows 執行階段 c + + 樣板程式庫類似 Active Template Library (ATL)，因為您可以用它來建立小型、 快速的 COM 物件。 Windows 執行階段 c + + 樣板程式庫和 ATL 也共用概念，例如在模組中，明確註冊介面，物件的定義，以及使用 factory 開放式建立物件。 您可能會想要 Windows 執行階段 c + + 樣板程式庫如果您熟悉 ATL  
  
 Windows 執行階段 c + + 樣板程式庫支援 COM 功能所需的 UWP 應用程式。 因此，它與 ATL 不同，因為後者省略直接支援 COM 功能，例如：  
  
-   彙總  
  
-   內建實作  
  
-   雙重介面 (`IDispatch`)  
  
-   標準列舉程式介面  
  
-   連接點  
  
-   Tear-Off 介面  
  
-   OLE 內嵌  
  
-   ActiveX 控制項  
  
-   COM+  
  
## <a name="concepts"></a>概念  
 Windows 執行階段 c + + 樣板程式庫提供代表某些基本概念的類型。 下列章節將說明這些類型：  
  
### <a name="comptr"></a>ComPtr  
 [ComPtr](../windows/comptr-class.md)是*智慧型指標*表示範本參數所指定之介面的型別。 使用 `ComPtr` 來宣告變數，以存取從介面衍生之物件的成員。 `ComPtr` 自動維護基礎介面指標的參考計數，並在參考計數歸零時釋放介面。  
  
### <a name="runtimeclass"></a>RuntimeClass  
 [RuntimeClass](../windows/runtimeclass-class.md)表示繼承一組指定之介面的具現化的類別。 A`RuntimeClass`物件可以提供的一或多個 Windows 執行階段 COM 介面或元件的弱式參考支援的組合。  
  
### <a name="module"></a>Module  
 [模組](../windows/module-class.md)表示相關物件的集合。 `Module` 物件管理 Class Factory 和註冊，前者會建立物件，後者讓其他應用程式使用物件。  
  
### <a name="callback"></a>回呼  
 [回呼](../windows/callback-function-windows-runtime-cpp-template-library.md)函式會建立的物件成員函式是事件處理常式 （回呼方法）。 使用 `Callback` 函式撰寫非同步作業。  
  
### <a name="eventsource"></a>EventSource  
 [EventSource](../windows/eventsource-class.md)用來管理*委派*事件處理常式。 使用 Windows 執行階段 c + + 樣板程式庫實作委派，並使用`EventSource`加入、 移除及叫用委派。  
  
### <a name="asyncbase"></a>AsyncBase  
 [AsyncBase](../windows/asyncbase-class.md)提供代表 Windows 執行階段非同步程式設計模型的虛擬方法。 覆寫這個類別中的成員，建立可以啟動、停止或檢查非同步作業進度的自訂類別。  
  
### <a name="ftmbase"></a>FtmBase  
 [FtmBase](../windows/ftmbase-class.md)表示無限制執行緒封送處理器物件。 `FtmBase` 建立全域介面表 (GIT)，並協助管理封送處理和 Proxy 物件。  
  
### <a name="weakref"></a>WeakRef  
 [WeakRef](../windows/weakref-class.md)是智慧型指標類型，表示*弱式參考*，會參考，可能或可能無法存取的物件。 A`WeakRef`物件可以用僅 Windows 執行階段，而不是傳統 com 使用。  
  
 `WeakRef` 物件通常代表其存在是由外部執行緒或應用程式所控制的物件。 例如， `WeakRef` 物件可以參考檔案物件。 在檔案開啟時， `WeakRef` 有效，而且參考的檔案是可存取的。 不過，在檔案關閉時， `WeakRef` 是無效，而且檔案無法存取。  
  
## <a name="related-topics"></a>相關主題  
  
|||  
|-|-|  
|[依類別目錄的索引鍵 Api](../windows/key-wrl-apis-by-category.md)|反白顯示主要的 Windows 執行階段 c + + 樣板程式庫類型、 函數和巨集。|  
|[參考資料](../windows/wrl-reference.md)|包含 Windows 執行階段 c + + 樣板程式庫的參考資訊。|  
|[快速參考 （Windows 執行階段和 Visual c + +）](http://go.microsoft.com/fwlink/p/?linkid=229180)|簡短描述 C + + /CX 支援 Windows 執行階段的功能。|  
|[在 Visual c + + 中使用 Windows 執行階段元件](http://go.microsoft.com/fwlink/p/?linkid=229155)|示範如何使用 C + + /CX 建立基本 Windows 執行階段元件。|