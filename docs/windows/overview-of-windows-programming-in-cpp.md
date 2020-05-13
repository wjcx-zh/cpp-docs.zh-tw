---
title: 使用 C++ 設計 Windows 應用程式概觀
ms.date: 09/17/2019
ms.assetid: efc691d7-21f3-47ae-ae56-cab999ccf59d
ms.openlocfilehash: 8ab7fbf7c955b1c828ef583aa639eda7409cf167
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359936"
---
# <a name="overview-of-windows-programming-in-c"></a>使用 C++ 設計 Windows 應用程式概觀

可以使用C++創建多個廣泛的Windows應用程式類別。 每個庫都有自己的程式設計模型和一組特定於 Windows 的庫,但 C++標準庫和第三方 C++庫都可以在任何庫中使用。

本節討論如何使用 Visual Studio 和 MFC/ATL 包裝庫創建 Windows 程式。 有關 Windows 平臺本身的文件,請參閱[Windows 文件](/windows/index)。

## <a name="command-line-console-applications"></a>命令列 (主控台)應用程式

C++控制台應用程式從控制台視窗中的命令列運行,並且只能顯示文本輸出。 有關詳細資訊,請參閱[創建C++控制台應用專案](../get-started/tutorial-console-cpp.md)。

## <a name="native-desktop-client-applications"></a>本機桌面用戶端應用程式

*本機桌面用戶端應用程式*是使用原始本機[Windows C API 或元件物件模型 (COM) API](/windows/win32/apiindex/windows-api-list)存取作業系統的 C 或 C++視窗應用程式。 這些 API 本身主要用 C 編寫。創建本機桌面應用的方法不止一種:您可以使用 Win32 API 直接程式設計,使用處理作業系統事件的 C 樣式訊息迴圈。 或者,您可以使用 Microsoft*基礎類*(MFC) 進行程式設計,這是一個稍微面向物件的C++庫,可以包裝 Win32。 與通用 Windows 平臺 (UWP) 相比,這兩種方法都不被視為"現代",但兩者都完全支援,並且當今世界有數百萬行代碼運行。 在視窗中運行的 Win32 應用程式要求開發人員在 Windows 過程函數中顯式處理 Windows 消息。 儘管名稱,Win32 應用程式可以編譯為 32 位元 (x86) 或 64 位元 (x64) 二進位檔案。 在視覺工作室 IDE 中,術語 x86 和 Win32 是同義詞。

要開始使用傳統的 Windows C++程式設計,請參閱[使用 Win32 入門和C++](/windows/win32/LearnWin32/learn-to-program-for-windows)。 瞭解 Win32 後,將更容易瞭解[MFC 桌面應用程式](../mfc/mfc-desktop-applications.md)。 有關使用複雜圖形的傳統C++桌面應用程式的範例,請參閱[Hilo:為 Windows 開發C++應用程式](https://msdn.microsoft.com/library/windows/desktop/ff708696.aspx)。

### <a name="c-or-net"></a>C++還是 .NET?

通常,C# 中的 .NET 程式設計不太複雜,不易出錯,並且具有比 Win32 或 MFC 更現代的面向物件的 API。 在大多數情況下,其性能遠遠不夠。 .NET 具有用於豐富圖形的 Windows 演示基礎 (WPF),您可以使用 Win32 和現代 Windows 執行時 API。 通常,我們建議您在需要時對桌面應用程式使用C++:

- 精確控制記憶體使用方式
- 最大的經濟消耗
- GPU 用於一般計算
- 存取 DirectX
- 大量使用標準C++庫

還可以將C++的功率和效率與 .NET 程式設計相結合。 您可以在 C# 中建立使用者介面,並使用 C++/CLI 使應用程式能夠使用本機 C++庫。 有關詳細資訊,請參閱[.NET 程式設計與C++/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)。

## <a name="com-components"></a>COM 元件

[元件物件模型 (COM)](/windows/win32/com/the-component-object-model)是一種規範,它允許用不同語言編寫的程式相互通訊。 許多 Windows 元件作為 COM 物件實現,並遵循物件創建、介面發現和物件破壞的標準 COM 規則。  使用來自C++桌面應用程式中的 COM 物件相對簡單,但編寫自己的 COM 物件更高級。 [活動範本庫 (ATL)](../atl/atl-com-desktop-components.md)提供宏和幫助器功能,可簡化 COM 開發。 有關詳細資訊,請參閱[ATL COM 桌面元件](../atl/atl-com-desktop-components.md)。

## <a name="universal-windows-platform-apps"></a>通用 Windows 平台應用程式

通用 Windows 平臺 (UWP) 是現代 Windows API。 UWP 應用在任何 Windows 10 設備上運行,使用 XAML 進行使用者介面,並且完全啟用觸控。 有關 UWP 的詳細[Guide to Windows Universal Apps](/windows/uwp/get-started/universal-application-platform-guide)資訊, 請參閱[什麼是通用 Windows 平臺 (UWP) 應用?](/windows/uwp/get-started/whats-a-uwp)

對 UWP 的原始C++支援包括 (1) C++/CX,一種帶有語法擴展的C++方言,或 (2) 基於標準C++和 COM 的 Windows 運行時庫 (WRL)。 仍然支援C++/CX 和 WRL。 對於新項目,我們建議[C++/WinRT,](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)它完全基於標準C++並提供更快的性能。

## <a name="desktop-bridge"></a>傳統型橋接器

在 Windows 10 中,您可以將現有桌面應用程式或 COM 物件打包為 UWP 應用,並添加 UWP 功能(如觸控)或從現代 Windows API 集中調用 API。 您還可以將 UWP 應用添加到 Visual Studio 中的桌面解決方案,並將它們打包在單個包中,並使用 Windows API 在它們之間進行通訊。

Visual Studio 2017 版本 15.4 及更高版本允許您創建 Windows 應用程式包專案,以大大簡化打包現有桌面應用程式的工作。 一些限制適用於桌面應用程式可以使用的註冊表調用或 API。 但是,在許多情況下,您可以創建備用代碼路徑,以便在應用包中運行時實現類似的功能。 如需詳細資訊，請參閱[傳統型橋接器](/windows/uwp/porting/desktop-to-uwp-root)。

## <a name="games"></a>遊戲

DirectX 遊戲可以在 PC 或 Xbox 上運行。 有關詳細資訊,請參閱[DirectX 圖像和遊戲](/windows/win32/directx)。

## <a name="sql-server-database-clients"></a>SQL 伺服器資料庫客戶端

要從本機代碼訪問 SQL Server 資料庫,請使用 ODBC 或 OLE DB。 如需詳細資訊，請參閱 [SQL Server Native Client](/sql/relational-databases/native-client/odbc/sql-server-native-client-odbc)。

## <a name="windows-device-drivers"></a>Windows 裝置驅動程式

驅動程式是低級元件,使應用程式和其他作業系統元件可以訪問來自硬體設備的數據。 有關詳細資訊,請參閱[Windows 驅動程式工具組 (WDK)。](/windows-hardware/drivers/index)

## <a name="windows-services"></a>Windows 服務

Windows*服務*是在後台運行的程式,很少或根本沒有使用者交互。 這些程式在 UNIX 系統上稱為*守護程式*。 如需詳細資訊，請參閱 [服務](/windows/win32/services/services)。

## <a name="sdks-libraries-and-header-files"></a>SDK、函式庫和標頭檔

可視化工作室包括 C 運行時庫 (CRT)、C++標準庫和其他特定於 Microsoft 的庫。 包含這些庫的標頭檔的大多數包含資料夾位於 [VC] 資料夾下的 Visual Studio 安裝目錄中。 Windows 和 CRT 標頭檔位於 Windows SDK 安裝資料夾中。

[Vcpkg 包管理員](../build/vcpkg.md)允許您方便地安裝數百個適用於 Windows 的第三方開源庫。

微軟庫包括:

- Microsoft Foundation Classes (MFC)：一種物件導向架構，用於建立具有豐富使用者介面 (例如按鈕、清單方塊、樹狀檢視和其他控制項) 的傳統 Windows 程式 (特別是企業應用程式)。 如需詳細資訊，請參閱 [MFC Desktop Applications](../mfc/mfc-desktop-applications.md)。

- Active Template Library (ATL)：用於建立 COM 元件的強大協助程式庫。 如需詳細資訊，請參閱 [ATL COM Desktop Components](../atl/atl-com-desktop-components.md)。

- C++ AMP (C++ Accelerated Massive Parallelism)：可讓您在 GPU 上執行高效能通用計算工作的程式庫。 如需詳細資訊，請參閱 [C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)。

- 並行執行階段：可簡化多核心 (multicore) 和數個核心 (many-core) 裝置的平行和非同步程式設計工作的程式庫。 如需詳細資訊，請參閱 [Concurrency Runtime](../parallel/concrt/concurrency-runtime.md)。

許多 Windows 程式設計案例也需要使用 Windows SDK，它包含了可讓您存取 Windows 作業系統元件的標頭檔。 默認情況下,Visual Studio 將 Windows SDK 安裝為 C++桌面工作負載的元件,從而支援通用 Windows 應用的開發。 要開發 UWP 應用,您需要 Windows 10 版本的 Windows SDK。 有關詳細資訊,請參閱[Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk)。 (有關早期版本的 Windows 的 Windows SDK 的詳細資訊,請參考[Windows SDK 存檔](https://developer.microsoft.com/windows/downloads/sdk-archive)。

**程式檔案 (x86)\Windows 工具套件**是已安裝的所有版本的 Windows SDK 的預設位置。

其他平台 (例如 Xbox 和 Azure) 有它們自己的 SDK，您可能必須安裝這些 SDK。 如需詳細資訊，請參閱 DirectX 開發人員中心和 Azure 開發人員中心。

## <a name="development-tools"></a>開發工具

Visual Studio 含有功能強大的機器碼偵錯工具、靜態分析工具、圖形偵錯工具、全功能的程式碼編輯器、單元測試支援，以及許多其他工具和公用程式。 有關詳細資訊,請參閱使用[Visual Studio 開始開發](/visualstudio/ide/get-started-developing-with-visual-studio),以及[可視化工作室中C++開發概述](../overview/overview-of-cpp-development.md)。

## <a name="in-this-section"></a>本節內容

|Title|描述|
|-----------|-----------------|
|[演練:創建標準C++計劃](walkthrough-creating-a-standard-cpp-program-cpp.md)| 創建 Windows 主控台應用程式。|
|[逐步解說：建立 Windows 傳統型應用程式 (C++)](walkthrough-creating-windows-desktop-applications-cpp.md)|創建本機 Windows 桌面應用程式。|
|[Windows 桌面精靈](windows-desktop-wizard.md)|使用嚮導創建新的 Windows 專案。|
|[Active Template Library (ATL)](../atl/atl-com-desktop-components.md)|使用 ATL 庫在 C++中創建 COM 元件。|
|[Microsoft Foundation Classes (MFC)](../mfc/mfc-desktop-applications.md)|使用 MFC 建立使用對話框和控制元件的大型或小型 Windows 應用程式|
|[ATL 和 MFC 共用類別](../atl-mfc-shared/atl-mfc-shared-classes.md)|使用在 ATL 和 MFC 中共用的 CString 等類。|
|[資料存取](../data/data-access-in-cpp.md)| OLE DB 與 ODBC|
|[文字和字串](../text/text-and-strings-in-visual-cpp.md)|Windows 上的各種字串類型。|
|[用於使用 DirectX 建立遊戲的資源](resources-for-creating-a-game-using-directx.md)
|[如何：在 Windows 桌面應用程式中使用 Windows 10 SDK](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Windows SDK|
|[使用資源檔](working-with-resource-files.md)|如何向桌面應用程式添加圖像、圖示、字串表和其他資源。|
|[用於使用 DirectX 建立遊戲的資源 (C++)](resources-for-creating-a-game-using-directx.md)|指向C++中創建遊戲的內容的連結。|
|[如何：在 Windows 桌面應用程式中使用 Windows 10 SDK](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|包含將您的專案設定為使用 Windows 10 SDK 建置的步驟。|
|[部署原生傳統型應用程式](deploying-native-desktop-applications-visual-cpp.md)|在 Windows 部署本機應用程式。|

## <a name="related-articles"></a>相關文章

|Title|描述|
|-----------|-----------------|
|[視覺工作室中的C++](../overview/visual-cpp-in-visual-studio.md)|VisualC++開發人員內容的父主題。|
[.NET 開發,帶C++/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|為本機C++庫創建包裝器,使其能夠與 .NET 應用程式和元件通信。|
|[.NET 和 UWP 的元件擴展](../extensions/component-extensions-for-runtime-platforms.md)|C++/CX 和 C++/CLI 共用的語法元素的引用。|
|[通用 Windows 應用程式 (C++)](../cppcx/universal-windows-apps-cpp.md)|使用C++/CX或Windows運行時範本庫 (WRL) 寫入 UWP 應用程式。|
|[適用於 COM 和 .NET 的 C++ 屬性](attributes/cpp-attributes-com-net.md)|使用 .NET 或 COM 的僅 Windows 程式設計的非標準屬性。|
