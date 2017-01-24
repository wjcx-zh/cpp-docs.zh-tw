---
title: "Windows Runtime C++ Template Library (WRL) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
ms.assetid: b915afce-553b-44a7-b8dc-0ab601758eb0
caps.latest.revision: 32
caps.handback.revision: 32
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Windows Runtime C++ Template Library (WRL)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[!INCLUDE[cppwrl](../windows/includes/cppwrl_md.md)] ([!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)]) 是提供低階方式撰寫和使用 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]元件的範本庫。  
  
## <a name="benefits"></a>優點  
 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 讓您更輕鬆地實作和使用 Component Object Model (COM) 元件。 它提供環境維護技術，如參考計數來管理物件的存留期，以及測試 `HRESULT` 值來判斷作業成功或失敗。 為了順利使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)]，您必須小心遵循這些規則和技術。  
  
 [!INCLUDE[cppwrt](../build/reference/includes/cppwrt_md.md)] ([!INCLUDE[cppwrt_short](../build/reference/includes/cppwrt_short_md.md)]) 是透過高階、以語言為基礎的方式使用 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 元件。 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 和 [!INCLUDE[cppwrt_short](../build/reference/includes/cppwrt_short_md.md)] 透過自動代表您執行環境維護工作，簡化 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 程式碼撰寫。  
  
 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 和 [!INCLUDE[cppwrt_short](../build/reference/includes/cppwrt_short_md.md)] 提供不同的優點。 建議使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 而不是 [!INCLUDE[cppwrt_short](../build/reference/includes/cppwrt_short_md.md)]，原因如下：  
  
-   [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 在 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]應用程式二進位介面 (ABI) 上沒有加入太多抽象性，讓您可以控制基礎程式碼，更有效建立或使用 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]應用程式開發介面。  
  
-   [!INCLUDE[cppwrt_short](../build/reference/includes/cppwrt_short_md.md)] 是以例外狀況代表 COM `HRESULT` 值。 如果您繼承了使用 COM 或沒有使用例外狀況的程式碼基底，您可能會發現 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 是與 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]一起使用比較自然的方式，因為您不需要使用例外狀況。  
  
    > [!NOTE]
    >  [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 使用 `HRESULT` 值，且不會擲回例外狀況。 此外， [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 使用智慧型指標和 RAII 模式，確保在您的應用程式程式碼擲回例外狀況時物件正確被終結。 如需智慧型指標和 RAII 的詳細資訊，請參閱 [智慧型指標](../cpp/smart-pointers-modern-cpp.md) 和 [物件自己的資源 (RAII)](../cpp/objects-own-resources-raii.md)。  
  
-   [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 的用途和設計受到 Active Template Library (ATL) 所啟發，這是一組簡化 COM 物件程式設計的範本架構 C++ 類別。 由於 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 使用 Standard C++ 包裝 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]，您可以更容易地將以 ATL 撰寫的許多現有 COM 元件移植至 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]並與之互動。 如果您已經知道 ATL，您可能會發現 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 程式設計更容易。  
  
## <a name="getting-started"></a>快速入門  
 以下是可幫助您立即開始使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 的一些資源。  
  
 [Windows 執行階段程式庫 (WRL)](http://channel9.msdn.com/Events/Windows-Camp/Developing-Windows-8-Metro-style-apps-in-Cpp/The-Windows-Runtime-Library-WRL-)  
 在這個 Channel 9 影片，進一步了解 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 如何協助您撰寫 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 應用程式，以及如何撰寫和使用 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 元件。  
  
 [如何︰ 啟動與使用 Windows 執行階段元件](../windows/how-to-activate-and-use-a-windows-runtime-component-using-wrl.md)  
 顯示如何使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 初始化 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] ，以及啟用和使用 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 元件。  
  
 [如何︰ 完成非同步作業](../windows/how-to-complete-asynchronous-operations-using-wrl.md)  
 顯示如何使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] ，當作業完成時啟動非同步作業和執行工作。  
  
 [如何︰ 處理事件](../windows/how-to-handle-events-using-wrl.md)  
 顯示如何使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 來訂閱和處理 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 物件的事件。  
  
 [逐步解說︰ 建立基本 Windows 執行階段元件](../windows/walkthrough-creating-a-basic-windows-runtime-component-using-wrl.md)  
 顯示如何使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 建立將兩個數字相加的基本 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 元件。 文件中也會示範如何從使用 JavaScript 的 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 應用程式引發事件及使用元件。  
  
 [逐步解說︰ 建立 Windows 市集應用程式使用 WRL 和媒體基礎](../windows/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation.md)  
 學習如何建立使用 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] Microsoft 媒體基礎 [的](http://msdn.microsoft.com/library/windows/apps/ms694197)應用程式。  
  
 [如何︰ 建立傳統 COM 元件](../windows/how-to-create-a-classic-com-component-using-wrl.md)  
 顯示如何使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 建立基本的 COM 元件，以及註冊和使用桌面應用程式 COM 元件的基本方法。  
  
 [如何︰ 直接執行個體化 WRL 元件](../windows/how-to-instantiate-wrl-components-directly.md)  
 了解如何使用 [Microsoft::WRL::Make](../windows/make-function.md) 和 [Microsoft::WRL::Details::MakeAndInitialize](../windows/makeandinitialize-function.md) 函式，從定義元件的模組中具現化元件。  
  
 [如何︰ 使用 winmdidl.exe 和 midlrt.exe windows 中繼資料建立.h 檔案](../windows/use-winmdidl-and-midlrt-to-create-h-files-from-windows-metadata.md)  
 顯示如何透過從 .winmd 中繼資料建立 IDL 檔案，使用 WRL 的自訂 Windows 執行階段元件。  
  
 [逐步解說︰ 使用工作和 XML HTTP 要求連線](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)  
 說明如何在 [應用程式中使用](http://msdn.microsoft.com/zh-tw/bbc11c4a-aecf-4d6d-8275-3e852e309908) IXMLHTTPRequest2 [和](http://msdn.microsoft.com/zh-tw/aa4b3f4c-6e28-458b-be25-6cce8865fc71) IXMLHTTPRequest2Callback [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 介面，以及將 HTTP GET 和 POST 要求傳送至 Web 服務的工作。  
  
 [Bing 地圖服務路線最佳化程式範例](http://code.msdn.microsoft.com/Bing-Maps-trip-optimizer-c4e037f7)  
 使用 `HttpRequest` 類別中定義 [逐步解說︰ 連接使用的工作和 XML HTTP 要求](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md) 完整的內容中 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 應用程式。  
  
 [使用 c + + 範例建立 Windows 執行階段 DLL 元件](http://code.msdn.microsoft.com/windowsapps/Creating-a-Windows-Runtime-6c399797)  
 顯示如何使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 建立同處理序 DLL 元件，以及從 C++/CX、JavaScript 和 C# 使用它。  
  
 [DirectX 彈珠迷宮遊戲範例](http://code.msdn.microsoft.com/windowsapps/DirectX-Marble-Maze-Game-e4806345)  
 示範如何在完整 3D 遊戲的內容中使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 管理 COM 元件的存留期，如 DirectX 和媒體基礎。  
  
 [從桌面應用程式範例傳送快顯通知](http://code.msdn.microsoft.com/windowsdesktop/Sending-toast-notifications-71e230a2)  
 示範如何使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 以處理來自桌面應用程式的快顯通知。  
  
## <a name="includecppwrlshorttokencppwrlshortmdmd-compared-to-atl"></a>[!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 和 ATL 比較  
 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 類似 Active Template Library (ATL)，因為您可以用它來建立小型、快速的 COM 物件。 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 和 ATL 也共用概念，例如在模組中定義物件、明確註冊介面，以及使用 Factory 開放式建立物件。 如果您熟悉 ATL，可能對 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 立即上手。  
  
 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 支援 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)]應用程式所需的 COM 功能。 因此，它與 ATL 不同，因為後者省略直接支援 COM 功能，例如：  
  
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
 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 提供代表某些基本概念的類型。 下列章節將說明這些類型：  
  
### <a name="comptr"></a>ComPtr  
 [ComPtr](../windows/comptr-class.md) 是 *智慧型指標* 類型，表示由範本參數指定之介面。 使用 `ComPtr` 來宣告變數，以存取從介面衍生之物件的成員。 `ComPtr` 自動維護基礎介面指標的參考計數，並在參考計數歸零時釋放介面。  
  
### <a name="runtimeclass"></a>RuntimeClass  
 [RuntimeClass](../windows/runtimeclass-class.md) 表示繼承一組指定之介面的具現化類別。 `RuntimeClass` 物件可提供一個或多個 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] COM 介面的支援組合，或提供元件的弱式參考。  
  
### <a name="module"></a>模組  
 [Module](../windows/module-class.md) 表示相關物件的集合。 `Module` 物件管理 Class Factory 和註冊，前者會建立物件，後者讓其他應用程式使用物件。  
  
### <a name="callback"></a>回呼  
 [Callback](../windows/callback-function-windows-runtime-cpp-template-library.md) 函式建立成員函式是事件處理常式的物件 (回呼方法)。 使用 `Callback` 函式撰寫非同步作業。  
  
### <a name="eventsource"></a>EventSource  
 [EventSource](../windows/eventsource-class.md) 用來管理「 *委派* 」(Delegate) 事件處理常式。 使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 實作委派，而使用 `EventSource` 加入、移除及叫用委派。  
  
### <a name="asyncbase"></a>AsyncBase  
 [AsyncBase](../windows/asyncbase-class.md) 提供代表 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 非同步程式撰寫模型的虛擬方法。 覆寫這個類別中的成員，建立可以啟動、停止或檢查非同步作業進度的自訂類別。  
  
### <a name="ftmbase"></a>FtmBase  
 [FtmBase](../windows/ftmbase-class.md) 代表無限制執行緒封送處理器物件。 `FtmBase` 建立全域介面表 (GIT)，並協助管理封送處理和 Proxy 物件。  
  
### <a name="weakref"></a>WeakRef  
 [WeakRef](../windows/weakref-class.md) 是代表 *弱式參考*的智慧型指標類型，會參考不一定可存取的物件。 `WeakRef` 物件只能供 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]使用，不可供傳統 COM 使用。  
  
 `WeakRef` 物件通常代表其存在是由外部執行緒或應用程式所控制的物件。 例如， `WeakRef` 物件可以參考檔案物件。 在檔案開啟時， `WeakRef` 有效，而且參考的檔案是可存取的。 不過，在檔案關閉時， `WeakRef` 是無效，而且檔案無法存取。  
  
## <a name="related-topics"></a>相關主題  
  
|||  
|-|-|  
|[類別庫專案範本](../windows/wrl-class-library-project-template.md)|說明如何存取 WRL 類別庫專案範本。 這個範本可協助簡化使用 Visual Studio 建立 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 元件之工作。|  
|[依類別目錄的索引鍵 Api](../windows/key-wrl-apis-by-category.md)|強調主要 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 類型、函式和巨集。|  
|[參考](../windows/wrl-reference.md)|包含 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)]的參考資訊。|  
|[快速參考 （Windows 執行階段和 Visual c + +）](http://go.microsoft.com/fwlink/?LinkId=229180)|簡要說明支援 [!INCLUDE[cppwrt_short](../build/reference/includes/cppwrt_short_md.md)] 的 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]功能。|  
|[在 Visual c + + 中使用 Windows 執行階段元件](http://go.microsoft.com/fwlink/?LinkId=229155)|說明如何使用 [!INCLUDE[cppwrt_short](../build/reference/includes/cppwrt_short_md.md)] 以建立基本 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 元件。|