---
title: 使用 C++ 設計 Windows 應用程式概觀
ms.date: 09/17/2019
ms.assetid: efc691d7-21f3-47ae-ae56-cab999ccf59d
ms.openlocfilehash: 96a03194059f59f57780bfd70cab3065d6a1aff0
ms.sourcegitcommit: 76cc69b482ada8ebf0837e8cdfd4459661f996dd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2019
ms.locfileid: "71127186"
---
# <a name="overview-of-windows-programming-in-c"></a>使用 C++ 設計 Windows 應用程式概觀

您可以使用C++建立幾個廣泛的 Windows 應用程式類別。 每個都有自己的程式設計模型和一組 Windows 特定程式庫C++ ，但標準程式庫和C++協力廠商程式庫可用於其中任何一種。 

本節討論如何使用 Visual Studio 和 MFC/ATL 包裝函式程式庫來建立 Windows 程式。 如需 Windows 平臺本身的相關檔，請參閱[windows 檔](/windows/index)。

## <a name="command-line-console-applications"></a>命令列（主控台）應用程式

C++主控台應用程式會從主控台視窗中的命令列執行，而且只能顯示文字輸出。 如需詳細資訊，請參閱[建立C++主控台應用程式專案](../get-started/tutorial-console-cpp.md)。

## <a name="native-desktop-client-applications"></a>原生桌面用戶端應用程式

*原生桌面用戶端應用程式*是一C++種 C 或視窗型應用程式，它會使用原始的原生[Windows C api 或元件物件模型（COM） api](/windows/win32/apiindex/windows-api-list)來存取作業系統。 這些 Api 的本身大部分都是以 C 撰寫。建立原生桌面應用程式的方法有很多種：您可以使用處理作業系統事件的 C 樣式訊息迴圈，直接使用 Win32 Api 進行程式設計。 或者，您可以使用*Microsoft Foundation* class （MFC）來進行程式設計，這是C++包裝 Win32 的輕微物件導向程式庫。 相較于通用 Windows 平臺（UWP），這兩種方法都不會被視為「現代化」，但這兩者仍然受到完整支援，且目前有數百萬個在世界各地執行的程式程式碼。 在視窗中執行的 Win32 應用程式需要開發人員在 Windows 程式函式內明確地處理 Windows 訊息。 無論名稱是什麼，Win32 應用程式都可以編譯為32位（x86）或64位（x64）二進位檔。 在 Visual Studio IDE 中，x86 和 Win32 這兩者都是同義。

若要開始使用傳統的C++ Windows 程式設計，請參閱[開始使用C++Win32 和](/windows/win32/LearnWin32/learn-to-program-for-windows)。 在您對 Win32 有一些瞭解之後，就可以更輕鬆地瞭解[MFC 桌面應用程式](../mfc/mfc-desktop-applications.md)。 如需使用複雜圖形的C++傳統桌面應用程式範例，請參閱[Hilo：開發C++適用于 Windows](https://msdn.microsoft.com/library/windows/desktop/ff708696.aspx)的應用程式。

### <a name="c-or-net"></a>C++或 .NET？

一般而言，中C#的 .net 程式設計比較不復雜、較不容易出錯，而且具有比 WIN32 或 MFC 更現代化的物件導向 API。 在大部分的情況下，其效能會比足夠的。 .NET 具備豐富圖形的 Windows Presentation Foundation （WPF），而且您可以同時使用 Win32 和新式 Windows 執行階段 API。 一般的規則是，建議您在C++需要時針對桌面應用程式使用：

- 精確控制記憶體使用量
- 電力耗用量的最高經濟效益
- 使用 GPU 進行一般計算
- 存取 DirectX
- 大量使用標準C++程式庫

您也可以結合的強大功能和效率C++與 .net 程式設計。 您可以在中C#建立使用者介面，並C++使用/cli 讓應用程式使用原生C++程式庫。 如需詳細資訊，請參閱[使用C++/cli 進行 .net 程式設計](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)。

## <a name="com-components"></a>COM 元件

[元件物件模型（COM）](/windows/win32/com/the-component-object-model)是一種規格，可讓以不同語言撰寫的程式彼此通訊。 許多 Windows 元件會實作為 COM 物件，並遵循標準 COM 規則來建立物件、介面探索和物件銷毀。  從C++桌面應用程式使用 COM 物件相當簡單，但撰寫自己的 COM 物件更為先進。 [Active Template Library （ATL）](../atl/atl-com-desktop-components.md)提供宏和 helper 函式，可簡化 COM 開發工作。 如需詳細資訊，請參閱[ATL COM desktop components](../atl/atl-com-desktop-components.md)。

## <a name="universal-windows-platform-apps"></a>通用 Windows 平台應用程式

通用 Windows 平臺（UWP）是現代化的 Windows API。 UWP 應用程式會在任何 Windows 10 裝置上執行、針對使用者介面使用 XAML，而且完全具備觸控功能。 如需 UWP 的詳細資訊，請參閱[什麼是通用 Windows 平臺（UWP）應用程式？](/windows/uwp/get-started/whats-a-uwp)和[Windows 通用應用程式指南](/windows/uwp/get-started/universal-application-platform-guide)。

UWP 的C++原始支援C++ C++包括（1）/cx、具有語法延伸的方言，或（2） Windows 執行階段程式庫（WRL），這是以標準C++和 COM 為基礎。 C++/CX 和 WRL 仍受到支援。 針對新的專案，我們建議[ C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)，這完全是以標準C++為基礎，並提供更快的效能。

## <a name="desktop-bridge"></a>桌面橋接器

在 Windows 10 中，您可以將現有的桌面應用程式或 COM 物件封裝為 UWP 應用程式，並新增 UWP 功能（例如觸控），或從新式 Windows API 集合呼叫 Api。 您也可以在 Visual Studio 中將 UWP 應用程式新增至桌面解決方案，並將其封裝在單一套件中，然後使用 Windows Api 在兩者之間進行通訊。

Visual Studio 2017 15.4 版和更新版本可讓您建立 Windows 應用程式封裝專案，以大幅簡化封裝現有桌面應用程式的工作。 有幾個限制適用于您的桌面應用程式可使用的登錄呼叫或 Api。 不過，在許多情況下，您可以建立替代的程式碼路徑，以在應用程式套件中執行時達到類似的功能。 如需詳細資訊，請參閱[傳統型橋接器](/windows/uwp/porting/desktop-to-uwp-root)。

## <a name="games"></a>遊戲

DirectX 遊戲可以在電腦或 Xbox 上執行。 如需詳細資訊，請參閱[DirectX 圖形和遊戲](/windows/win32/directx)。

## <a name="sql-server-database-clients"></a>SQL Server 資料庫用戶端

若要從機器碼存取 SQL Server 資料庫，請使用 ODBC 或 OLE DB。 如需詳細資訊，請參閱 [SQL Server Native Client](/sql/relational-databases/native-client/odbc/sql-server-native-client-odbc)。

## <a name="windows-device-drivers"></a>Windows 裝置驅動程式

驅動程式是低層級的元件，可讓應用程式和其他作業系統元件存取硬體裝置的資料。 如需詳細資訊，請參閱[Windows 驅動程式套件（WDK）](/windows-hardware/drivers/index)。

## <a name="windows-services"></a>Windows 服務

Windows*服務*是一種程式，可以在背景中執行，幾乎不需要使用者互動。 這些程式稱為 UNIX 系統上的*守護*程式。 如需詳細資訊，請參閱[服務](/windows/win32/services/services)。

## <a name="sdks-libraries-and-header-files"></a>Sdk、程式庫和標頭檔

Visual Studio 包括 C 執行時間程式庫（CRT）、 C++標準程式庫和其他 Microsoft 特定程式庫。 包含這些程式庫之標頭檔的大多數 include 資料夾，都位於 [\VC\] 資料夾下的 Visual Studio 安裝目錄中。 Windows 和 CRT 標頭檔可在 Windows SDK 安裝資料夾中找到。

[Vcpkg 套件管理員](../build/vcpkg.md)可讓您輕鬆地安裝數百個適用于 Windows 的協力廠商開放原始碼程式庫。

Microsoft 程式庫包括：

- Microsoft Foundation class （MFC）：物件導向架構，用於建立傳統 Windows 程式（特別是企業應用程式），其中具有功能按鈕、清單方塊、樹狀檢視和其他控制項的豐富使用者介面。 如需詳細資訊，請參閱 [MFC Desktop Applications](../mfc/mfc-desktop-applications.md)。

- Active Template Library （ATL）：用來建立 COM 元件的強大 helper 程式庫。 如需詳細資訊，請參閱 [ATL COM Desktop Components](../atl/atl-com-desktop-components.md)。

- C++AMP （C++加速的大規模平行處理）：可在 GPU 上啟用高效能一般計算工作的程式庫。 如需詳細資訊，請參閱 [C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)。

- 並行執行階段：一種程式庫，可簡化平行和非同步程式設計的核心和多核心裝置的工作。 如需詳細資訊，請參閱 [Concurrency Runtime](../parallel/concrt/concurrency-runtime.md)。

許多 Windows 程式設計案例也需要使用 Windows SDK，它包含了可讓您存取 Windows 作業系統元件的標頭檔。 根據預設，Visual Studio 會將 Windows SDK 安裝為C++桌面工作負載的元件，以啟用通用 Windows 應用程式的開發。 若要開發 UWP 應用程式，您需要 Windows 10 版的 Windows SDK。 如需相關資訊，請參閱[Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk)。 （如需舊版 Windows 之 Windows Sdk 的詳細資訊，請參閱[Windows SDK](https://developer.microsoft.com/windows/downloads/sdk-archive)封存）。

**Program Files （x86） \Windows 套件**是您已安裝之所有 Windows SDK 版本的預設位置。

其他平台 (例如 Xbox 和 Azure) 有它們自己的 SDK，您可能必須安裝這些 SDK。 如需詳細資訊，請參閱 DirectX 開發人員中心和 Azure 開發人員中心。

## <a name="development-tools"></a>開發工具

Visual Studio 含有功能強大的機器碼偵錯工具、靜態分析工具、圖形偵錯工具、全功能的程式碼編輯器、單元測試支援，以及許多其他工具和公用程式。 如需詳細資訊，請參閱[開始使用 Visual Studio 進行開發](/visualstudio/ide/get-started-developing-with-visual-studio)和[Visual Studio C++中的開發總覽](../overview/overview-of-cpp-development.md)。

## <a name="in-this-section"></a>本節內容
|標題|描述|
|-----------|-----------------|
|[逐步解說：建立標準 C++ 程式](walkthrough-creating-a-standard-cpp-program-cpp.md)| 建立 Windows 主控台應用程式。|
|[逐步解說：建立 Windows 傳統型應用程式 (C++)](walkthrough-creating-windows-desktop-applications-cpp.md)|建立原生 Windows 桌面應用程式。|
|[Windows 傳統型精靈](windows-desktop-wizard.md)|使用 wizard 建立新的 Windows 專案。|
|[Active Template Library (ATL)](../atl/atl-com-desktop-components.md)|在中C++，使用 ATL 程式庫來建立 COM 元件。|
|[Microsoft Foundation Classes (MFC)](../mfc/mfc-desktop-applications.md)|使用 MFC 以對話方塊和控制項建立大型或小型 Windows 應用程式|
|[ATL 和 MFC 共用類別](../atl-mfc-shared/atl-mfc-shared-classes.md)|使用 ATL 和 MFC 中共用之 CString 之類的類別。|
|[資料存取](../data/data-access-in-cpp.md)| OLE DB 和 ODBC|
|[文字和字串](../text/text-and-strings-in-visual-cpp.md)|Windows 上的各種字串類型。|
|[用於使用 DirectX 建立遊戲的資源](resources-for-creating-a-game-using-directx.md)
|[如何：在 Windows 傳統型應用程式中使用 Windows 10 SDK](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Windows SDK|
|[使用資源檔](working-with-resource-files.md)|如何將影像、圖示、字串資料表和其他資源新增至桌面應用程式。|
|[使用 DirectX 建立遊戲的資源（C++）](resources-for-creating-a-game-using-directx.md)|在中C++建立遊戲之內容的連結。|
|[如何：在 Windows 傳統型應用程式中使用 Windows 10 SDK](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|包含將您的專案設定為使用 Windows 10 SDK 建置的步驟。|
|[部署原生傳統型應用程式](deploying-native-desktop-applications-visual-cpp.md)|在 Windows 上部署原生應用程式。|

## <a name="related-articles"></a>相關文章

|標題|描述|
|-----------|-----------------|
|[Visual Studio 中的 C++](../overview/visual-cpp-in-visual-studio.md)|Visual C++ developer content 的父主題。|
[使用 C++/CLI 進行 .NET 開發](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|建立原生C++程式庫的包裝函式，讓它能夠與 .net 應用程式和元件通訊。|
|[適用於.NET 和 UWP 的元件延伸模組](../extensions/component-extensions-for-runtime-platforms.md)|/Cx 和C++ C++/cli 所共用之語法元素的參考|
|[通用 Windows 應用程式 (C++)](../cppcx/universal-windows-apps-cpp.md)|使用/Cx 或 Windows 執行階段C++範本庫（WRL）來撰寫 UWP 應用程式。|
|[適用於 COM 與 .NET 的 C++ 屬性](attributes/cpp-attributes-com-net.md)|僅限 Windows 使用 .NET 或 COM 進行程式設計的非標準屬性。|
