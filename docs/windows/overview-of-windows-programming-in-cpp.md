---
title: 使用 C++ 設計 Windows 應用程式概觀
ms.date: 03/28/2019
ms.assetid: efc691d7-21f3-47ae-ae56-cab999ccf59d
ms.openlocfilehash: 48c7f419b6c69955ab25db528c8d3d86a7249391
ms.sourcegitcommit: 14b292596bc9b9b883a9c58cd3e366b282a1f7b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60124937"
---
# <a name="overview-of-windows-programming-in-c"></a>使用 C++ 設計 Windows 應用程式概觀

有數種廣泛的類別，您可以使用建立的 Windows 應用程式的C++。 每個都有它自己的程式設計模型和設定 Windows 特定文件庫，但C++標準程式庫，以及第三方C++程式庫可用在任何一個。 

## <a name="command-line-console-applications"></a>命令列 （主控台） 應用程式

C++主控台應用程式從命令列主控台視窗中執行，而且可以顯示僅限文字輸出。 如需詳細資訊，請參閱 <<c0> [ 主控台應用程式](console-applications-in-visual-cpp.md)。
 
## <a name="native-desktop-client-applications"></a>原生桌面用戶端應用程式

詞彙*原生桌面用戶端應用程式*指的是 C 或C++視窗型的應用程式，會使用原始的原生[Windows C Api 及/或 COM Api](/windows/desktop/apiindex/windows-api-list)來存取作業系統。 這些 Api 大部分是以 c 撰寫本身就是在建立這類應用程式時，您可以選擇直接對 C 樣式的訊息迴圈處理作業系統事件進行程式設計，或使用*Microsoft Foundation Classes* (MFC)C++包裝的程式庫Win32 是有點物件導向的方式。 這兩種方法會被視為 「 現代化 」 相較於通用 Windows 平台 （請參閱下文），但同時仍可完全支援，以及數以百萬計的世界中目前執行的程式碼行。 在視窗中執行的 Win32 應用程式會要求開發人員明確地使用 Windows 程序函式內的 Windows 訊息。 名稱，即使 Win32 應用程式可以編譯為 32 位元 (x86) 或 64 位元 (x64) 二進位。 在 Visual Studio IDE 中，Win32 與條款 x86 的意義相同。

若要開始使用傳統的 WindowsC++進行程式設計，請參閱[開始使用 Win32 和C++ ](/windows/desktop/LearnWin32/learn-to-program-for-windows)。 取得 Win32 有一些了解之後，它能夠更輕鬆地了解[MFC Desktop Applications](/mfc/mfc-desktop-applications)。 如需傳統的範例C++桌面應用程式，會使用複雜的圖形，請參閱[Hilo:開發C++適用於 Windows 應用程式](https://msdn.microsoft.com/library/windows/desktop/ff708696.aspx)。

### <a name="c-or-net"></a>C++或.NET 嗎？ 

對於大部分的桌面應用程式案例 (亦即，不是目標的 UWP)，請考慮使用C#來建立使用者介面。 這是因為.NET 進行程式設計很通常較不複雜且較不容易發生錯誤，且具有更現代化物件導向 API，比 Win32 或 MFC。 在大部分情況下，其效能已綽綽有餘。 .NET 的功能豐富的圖形的 Windows Presentation Foundation (WPF)，以及您可以使用 Win32，以及新式 Windows 執行階段 API （請參閱下面的 UWP）。 一般而言，我們建議使用C++桌面應用程式，當您需要：

- 精確地控制記憶體使用量
- 功率耗用量在最經濟
- 一般運算的 GPU 使用量
- 存取 DirectX
- 標準的繁重使用量C++程式庫

您可以建立中的使用者介面C#，並使用C++若要啟用的應用程式使用原生 /CLIC++程式庫。 如需詳細資訊，請參閱 <<c0> [ 使用的.NET 程式設計C++/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)。</c0>

## <a name="com-components"></a>COM 元件

[元件物件模型 (COM)](/windows/desktop/com/the-component-object-model)是一種規格，可讓以與彼此進行通訊的不同語言撰寫的程式。 許多 Windows 元件會實作為 COM 物件，並遵循標準的 COM 規則，以便建立物件，探索和物件解構的介面。  使用 COM 物件從C++桌面應用程式是相當簡單，但更進階撰寫您自己的 COM 物件。 [Active Template Library (ATL)](../atl/atl-com-desktop-components.md)提供巨集和簡化 COM 開發的協助程式函式。 如需詳細資訊，請參閱 < [ATL COM 桌面元件](../atl/atl-com-desktop-components.md)。

## <a name="windows-universal-apps"></a>Windows 通用應用程式

通用 Windows 平台 (UWP) 是現代 Windows API。 UWP 應用程式在任何 Windows 10 裝置上執行 XAML 用於使用者介面，則為完全支援觸控功能。 如需 UWP 的詳細資訊，請參閱[通用 Windows 平台 (UWP) 應用程式是什麼？](/windows/uwp/get-started/whats-a-uwp)並[Windows 通用應用程式指南](/windows/uwp/get-started/universal-application-platform-guide)。

原始C++UWP 所組成 (1) 的支援C++的方言，/CXC++語法延伸模組，或 （2) Windows 執行階段範本庫 (WRL) 是以標準為基礎的C++和 com。 同時C++/CX WRL 仍受支援。 我們建議針對新的專案[ C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)這完全以標準為基礎C++，並提供更快的效能。 

## <a name="desktop-bridge"></a>傳統型橋接器

在 Windows 10 中，您可以封裝您現有的桌面應用程式或為 UWP 應用程式的 COM 物件和新增 UWP 的功能，例如觸控，或從最新的 Windows API 集呼叫 Api。 您也可以新增至桌面的方案在 Visual Studio 中，並將它們在單一封裝，並使用 Windows Api 來彼此之間通訊的封裝中的 UWP 應用程式。

在 Visual Studio 2017 15.4 版和更新版本，您可以建立 Windows 應用程式封裝專案，大幅簡化封裝現有傳統型應用程式的工作。 有一些限制相對於呼叫哪些登錄或桌面應用程式的 Api 使用，但在許多情況下，您可以建立替代的程式碼路徑，以達到類似的功能，在執行中應用程式套件時。 如需詳細資訊，請參閱[傳統型橋接器](/windows/uwp/porting/desktop-to-uwp-root)。

## <a name="games"></a>遊戲

DirectX 遊戲可以在 PC 或 Xbox 上執行。 如需詳細資訊，請參閱 < [DirectX 圖形和遊戲](/windows/desktop/directx)。

## <a name="sql-server-database-clients"></a>SQL Server 資料庫用戶端

若要從原生程式碼中存取 SQL Server 資料庫，請使用 ODBC 或 OLE DB。 如需詳細資訊，請參閱 [SQL Server Native Client](/sql/relational-databases/native-client/odbc/sql-server-native-client-odbc)。

## <a name="windows-device-drivers"></a>Windows 裝置驅動程式

驅動程式是低層級的元件，可讓硬體裝置上的資料存取應用程式存取和其他作業系統元件。 如需詳細資訊，請參閱 < [Windows Driver Kit (WDK)](/windows-hardware/drivers/index)。

## <a name="windows-services"></a>Windows 服務

Windows*服務*是可以在幾乎不需要使用者互動的背景中執行的程式。 在 UNIX 中這些稱為*精靈*。 如需詳細資訊，請參閱 < [Services](/windows/desktop/services/services)。

## <a name="sdks-libraries-and-header-files"></a>Sdk、 程式庫和標頭檔

Visual Studio 包含 C 執行階段程式庫 (CRT)，C++標準程式庫和其他 Microsoft 特定程式庫。 包含這些程式庫標頭檔的 include 資料夾位於在 Visual Studio 安裝目錄下的 \VC\ 資料夾中，或在 CRT，在 Windows SDK 安裝資料夾的情況下。

您可以使用[Vcpkg 套件管理員](../build/vcpkg.md)方便的 Windows 中安裝數百個第三方開放原始碼程式庫。

Microsoft 程式庫包括：

- Microsoft Foundation Classes (MFC):物件導向的架構，用於建立傳統 Windows 程式 — 尤其是企業應用程式，這些功能的按鈕、 清單方塊、 樹狀檢視，以及其他控制項具有豐富的使用者介面。 如需詳細資訊，請參閱 [MFC Desktop Applications](../mfc/mfc-desktop-applications.md)。

- Active Template Library (ATL):用來建立 COM 元件的功能強大的協助程式程式庫。 如需詳細資訊，請參閱 [ATL COM Desktop Components](../atl/atl-com-desktop-components.md)。

- C++P (C++ Accelerated Massive Parallelism):文件庫，可讓高效能通用計算的工作在 GPU 上。 如需詳細資訊，請參閱 [C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)。

- 並行執行階段：文件庫，可簡化多核心和多核心裝置的平行和非同步程式設計的工作。 如需詳細資訊，請參閱 [Concurrency Runtime](../parallel/concrt/concurrency-runtime.md)。

許多 Windows 程式設計案例也需要使用 Windows SDK，它包含了可讓您存取 Windows 作業系統元件的標頭檔。 根據預設，Visual Studio 會安裝 Windows SDK 元件的C++可讓開發通用 Windows 應用程式的桌面工作負載。 若要開發 UWP 應用程式，您需要 Windows 10 的 Windows SDK 版本。 如需資訊，請參閱[Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk)。 (如需舊版 Windows 的 Windows Sdk 的詳細資訊，請參閱[Windows SDK 封存](https://developer.microsoft.com/windows/downloads/sdk-archive))。

**程式檔案 (x86) \Windows 套件**是您已安裝的 Windows sdk 的所有版本的預設位置。

其他平台 (例如 Xbox 和 Azure) 有它們自己的 SDK，您可能必須安裝這些 SDK。 如需詳細資訊，請參閱 DirectX 開發人員中心和 Azure 開發人員中心。

## <a name="development-tools"></a>開發工具

Visual Studio 含有功能強大的機器碼偵錯工具、靜態分析工具、圖形偵錯工具、全功能的程式碼編輯器、單元測試支援，以及許多其他工具和公用程式。 如需詳細資訊，請參閱 <<c0> [ 開始使用 Visual Studio 進行開發](/visualstudio/ide/get-started-developing-with-visual-studio)，並[概觀C++Visual Studio 中的開發](../overview/overview-of-cpp-development.md)。</c0>

## <a name="in-this-section"></a>本節內容
|標題|描述|
|-----------|-----------------|
|[逐步解說：建立標準 C++ 程式](walkthrough-creating-a-standard-cpp-program-cpp.md)| 建立 Windows 主控台應用程式。|
|[逐步解說：建立 Windows 傳統型應用程式 (C++)](walkthrough-creating-windows-desktop-applications-cpp.md)|建立簡單的 Windows 桌面應用程式。|
|[Windows 傳統型精靈](windows-desktop-wizard.md)|使用精靈來建立新的 Windows 專案。|
|[Active Template Library (ATL)](../atl/TOC.md)|使用 ATL 程式庫來建立 COM 元件，在C++。|
|[Microsoft Foundation Classes (MFC)](../mfc/TOC.md)|使用 MFC 來建立使用對話方塊和控制項的大型或小型的 Windows 應用程式|
|[ATL 和 MFC 共用類別](../atl-mfc-shared/TOC.md)|使用 CString 例如 ATL 和 MFC 中所共用的類別。|
|[資料存取](../data/data-access-in-cpp.md)| OLE DB 和 ODBC|
|[文字和字串](../text/text-and-strings-in-visual-cpp.md)|在 Windows 上的各種字串類型。|
|[用於使用 DirectX 建立遊戲的資源](resources-for-creating-a-game-using-directx.md)
|[如何：在 Windows 傳統型應用程式中使用 Windows 10 SDK](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Windows SDK|
|[使用資源檔](working-with-resource-files.md)|如何將影像、 圖示、 字串資料表和其他資源新增到桌面應用程式。|
|[使用 DirectX 建立遊戲的資源 (C++)](resources-for-creating-a-game-using-directx.md)|建立遊戲中的內容連結C++。|
|[如何：在 Windows 傳統型應用程式中使用 Windows 10 SDK](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|包含將您的專案設定為使用 Windows 10 SDK 建置的步驟。|
|[部署原生傳統型應用程式](deploying-native-desktop-applications-visual-cpp.md)|部署在 Windows 上的原生應用程式。|


## <a name="related-articles"></a>相關文章

|標題|描述|
|-----------|-----------------|
|[Visual C++](../overview/visual-cpp-in-visual-studio.md)|視覺效果的父主題C++開發人員內容。|
[使用 C++/CLI 進行 .NET 開發](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|建立原生包裝函式C++程式庫，讓它與.NET 應用程式和元件之間的通訊。|
|[適用於.NET 和 UWP 的元件延伸模組](../extensions/component-extensions-for-runtime-platforms.md)|共用的語法元素的參考C++/CX 和C++/CLI。|
|[通用 Windows 應用程式 (C++)](universal-windows-apps-cpp.md)|撰寫 UWP 應用程式使用C++/CX 或 Windows 執行階段範本庫 (WRL)。|
|[適用於 COM 與 .NET 的 C++ 屬性](attributes/cpp-attributes-com-net.md)|非標準的屬性，僅限 Windows 的程式設計，使用.NET 或 com。|

