---
title: 使用 C++ 設計 Windows 應用程式概觀
ms.date: 11/15/2018
ms.assetid: efc691d7-21f3-47ae-ae56-cab999ccf59d
ms.openlocfilehash: 6338b390b11c58f3ebac2af1bb568ea3c3470cd1
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57810441"
---
# <a name="overview-of-windows-programming-in-c"></a>使用 C++ 設計 Windows 應用程式概觀

有數種廣泛的類別，您可以建立使用 c + + 的 Windows 應用程式。 每個都有它自己的程式設計模型和組 Windows 特定程式庫，但 c + + 標準程式庫，以及第三方 c + + 程式庫可用在任何一個。 

## <a name="command-line-console-applications"></a>命令列 （主控台） 應用程式

C + + 主控台應用程式從命令列主控台視窗中執行，並且可以顯示僅限文字輸出。 如需詳細資訊，請參閱 <<c0> [ 主控台應用程式](console-applications-in-visual-cpp.md)。
 
## <a name="native-desktop-client-applications"></a>原生桌面用戶端應用程式

詞彙*原生桌面用戶端應用程式*指的 C 或 c + + 視窗型應用程式會使用原始 Windows Win32 Api 來存取作業系統。 這些 Api 大部分是以 c 撰寫本身就是在建立這類應用程式時，您可以選擇直接對 C 樣式的訊息迴圈處理作業系統事件進行程式設計，或使用*Microsoft Foundation Classes* (MFC)，包裝 Win32 的 c + + 程式庫已比較的物件導向的方式。 這兩種方法會被視為 「 現代化 」 相較於通用 Windows 平台 （請參閱下文），但同時仍可完全支援，以及數以百萬計的世界中目前執行的程式碼行。

若要開始使用傳統 Windows c + + 程式設計，請參閱[開始使用 Win32 和 c + +](/windows/desktop/LearnWin32/learn-to-program-for-windows)。 取得 Win32 有一些了解之後，它能夠更輕鬆地了解[MFC Desktop Applications](/mfc/mfc-desktop-applications)。 如需傳統 c + + 桌面應用程式使用複雜的圖形的範例，請參閱[Hilo:開發 Windows 的 c + + 應用程式](https://msdn.microsoft.com/library/windows/desktop/ff708696.aspx)。

### <a name="c-or-net"></a>C + + 或.NET 嗎？ 

對於大部分的桌面應用程式案例 (亦即，不是目標的 UWP)，請考慮使用C#和.NET。 這是因為.NET 進行程式設計很通常較不複雜且較不容易發生錯誤，且具有更現代化物件導向 API，比 Win32 或 MFC。 在大部分情況下，其效能已綽綽有餘。 .NET 的功能豐富的圖形的 Windows Presentation Foundation (WPF)，以及您可以使用 Win32，以及新式 Windows 執行階段 API （請參閱下面的 UWP）。 一般而言，我們建議使用 c + + 的桌面應用程式，當您需要：

- 精確地控制記憶體使用量
- 功率耗用量在最經濟
- 一般運算的 GPU 使用量
- 存取 DirectX
- 標準 c + + 程式庫的繁重使用量

## <a name="com-components"></a>COM 元件

Windows 作業系統中的許多部分以在元件物件模型 (COM) 會定義一種二進位的標準，可讓元件能從任何電腦語言撰寫的用戶端應用程式取用。 在 c + + 中，您可以使用 Active Template Library (ATL) 以簡化建立您自己的 COM 元件的工作。 如需詳細資訊，請參閱 <<c0> [ 元件物件模型 (COM)](/windows/desktop/com/component-object-model--com--portal)並[ATL COM 桌面元件](../atl/atl-com-desktop-components.md)。

## <a name="windows-universal-apps"></a>Windows 通用應用程式

通用 Windows 平台 (UWP) 是現代 Windows API。 UWP 應用程式在任何 Windows 10 裝置上執行 XAML 用於使用者介面，則為完全支援觸控功能。 如需 UWP 的詳細資訊，請參閱[通用 Windows 平台 (UWP) 應用程式是什麼？](/windows/uwp/get-started/whats-a-uwp)並[Windows 通用應用程式指南](/windows/uwp/get-started/universal-application-platform-guide)。

包含原始 c + + 支援適用於 UWP 的 （1） C + + /CX 中，與 c + + 語法延伸模組或 （2) Windows 執行階段範本庫 (WRL) 標準的 c + + 和 COM 為基礎的方言 這兩個 C + + /CX 和 WRL 仍受到支援。 我們建議針對新的專案[C + + /cli WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)可完全以標準 c + + 為基礎，並提供更快的效能。 

適用於 Windows 10，您可以將封裝您現有 c + + 桌面應用程式-適用於透過 Microsoft Store 部署。 如需詳細資訊，請參閱 <<c0> [ 桌面應用程式 （傳統型橋接器） 封裝](/windows/uwp/porting/desktop-to-uwp-root)。

## <a name="games"></a>遊戲

DirectX 遊戲可以在 PC 或 Xbox 上執行。 如需詳細資訊，請參閱 < [DirectX 圖形和遊戲](/windows/desktop/directx)。

## <a name="net-wrappers-for-c-libraries"></a>C + + 程式庫的.NET 包裝函式

您可以使用 C + + /cli CLI 來建立 interop 層，可讓使用原生 c + + 程式庫的.NET 程式碼。 如需詳細資訊，請參閱 < [.NET 程式設計使用 C + + /cli CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)。

## <a name="sql-server-database-clients"></a>SQL Server 資料庫用戶端

若要從原生程式碼中存取 SQL Server 資料庫，請使用 ODBC 或 OLE DB。 如需詳細資訊，請參閱 [SQL Server Native Client](/sql/relational-databases/native-client/odbc/sql-server-native-client-odbc)。

## <a name="windows-device-drivers"></a>Windows 裝置驅動程式

驅動程式是低層級的元件，可讓硬體裝置上的資料存取應用程式存取和其他作業系統元件。 如需詳細資訊，請參閱 < [Windows Driver Kit (WDK)](/windows-hardware/drivers/index)。

## <a name="windows-services"></a>Windows 服務

Windows*服務*是可以在幾乎不需要使用者互動的背景中執行的程式。 在 UNIX 中這些稱為*精靈*。 如需詳細資訊，請參閱 < [Services](/windows/desktop/services/services)。

## <a name="sdks-libraries-and-header-files"></a>Sdk、 程式庫和標頭檔

Visual Studio 包含 C 執行階段程式庫 (CRT)、 c + + 標準程式庫和其他 Microsoft 特定程式庫。 包含這些程式庫標頭檔的 include 資料夾位於在 Visual Studio 安裝目錄下的 \VC\ 資料夾中，或在 CRT，在 Windows SDK 安裝資料夾的情況下。

您可以使用[Vcpkg 套件管理員](../vcpkg.md)方便的 Windows 中安裝數百個第三方開放原始碼程式庫。

Microsoft 程式庫包括：

- Microsoft Foundation Classes (MFC):物件導向的架構，用於建立傳統 Windows 程式 — 尤其是企業應用程式，這些功能的按鈕、 清單方塊、 樹狀檢視，以及其他控制項具有豐富的使用者介面。 如需詳細資訊，請參閱 [MFC Desktop Applications](../mfc/mfc-desktop-applications.md)。

- Active Template Library (ATL):用來建立 COM 元件的功能強大的協助程式程式庫。 如需詳細資訊，請參閱 [ATL COM Desktop Components](../atl/atl-com-desktop-components.md)。

- C + + AMP (c + + Accelerated Massive Parallelism):文件庫，可讓高效能通用計算的工作在 GPU 上。 如需詳細資訊，請參閱 [C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)。

- 並行執行階段：文件庫，可簡化多核心和多核心裝置的平行和非同步程式設計的工作。 如需詳細資訊，請參閱 [Concurrency Runtime](../parallel/concrt/concurrency-runtime.md)。

許多 Windows 程式設計案例也需要使用 Windows SDK，它包含了可讓您存取 Windows 作業系統元件的標頭檔。 根據預設，Visual Studio 會安裝 Windows SDK 的 c + + 桌面工作負載，讓您能夠開發通用 Windows 應用程式的元件。 若要開發 UWP 應用程式，您需要 Windows 10 的 Windows SDK 版本。 如需資訊，請參閱[Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk)。 (如需舊版 Windows 的 Windows Sdk 的詳細資訊，請參閱[Windows SDK 封存](https://developer.microsoft.com/windows/downloads/sdk-archive))。

**程式檔案 (x86) \Windows 套件**是您已安裝的 Windows sdk 的所有版本的預設位置。

其他平台 (例如 Xbox 和 Azure) 有它們自己的 SDK，您可能必須安裝這些 SDK。 如需詳細資訊，請參閱 DirectX 開發人員中心和 Azure 開發人員中心。

## <a name="development-tools"></a>開發工具

Visual Studio 含有功能強大的機器碼偵錯工具、靜態分析工具、圖形偵錯工具、全功能的程式碼編輯器、單元測試支援，以及許多其他工具和公用程式。 如需詳細資訊，請參閱 <<c0> [ 開始使用 Visual Studio 進行開發](/visualstudio/ide/get-started-developing-with-visual-studio)，並[在 Visual Studio 中開發的 c + + 的概觀](../overview-of-cpp-development.md)。

## <a name="in-this-section"></a>本節內容
|標題|描述|
|-----------|-----------------|
|[以 C++ 撰寫的 Windows 傳統型應用程式](desktop-applications-visual-cpp.md)| 如何建立傳統桌面應用程式。|
|[Active Template Library (ATL)](../atl/TOC.md)|使用 ATL 程式庫來建立 c + + 中的 COM 元件。|
|[Microsoft Foundation Classes (MFC)](../mfc/TOC.md)|使用 MFC 來建立使用對話方塊和控制項的大型或小型的 Windows 應用程式|
|[ATL 和 MFC 共用類別](../atl-mfc-shared/TOC.md)|使用 CString 例如 ATL 和 MFC 中所共用的類別。|
|[使用 C++/CLI 進行 .NET 開發](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|建立原生 c + + 程式庫，讓它與.NET 應用程式和元件通訊的包裝函式。|
|[適用於.NET 和 UWP 的元件延伸模組](component-extensions-for-runtime-platforms.md)|參考的語法項目共用的 C + + /CX 和 C + + /cli CLI。|
|[通用 Windows 應用程式 (C++)](universal-windows-apps-cpp.md)|撰寫 UWP 應用程式使用 C + + /CX 或 Windows 執行階段範本庫 (WRL)。|
|[適用於 COM 與 .NET 的 C++ 屬性](attributes/cpp-attributes-com-net.md)|非標準的屬性，僅限 Windows 的程式設計，使用.NET 或 com。|

## <a name="related-articles"></a>相關文章

|標題|描述|
|-----------|-----------------|
|[Visual C++](../visual-cpp-in-visual-studio.md)|Visual c + + 開發人員內容的父主題。|
