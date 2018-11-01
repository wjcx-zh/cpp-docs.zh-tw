---
title: 使用 C++ 設計 Windows 應用程式概觀
ms.date: 04/06/2018
ms.assetid: efc691d7-21f3-47ae-ae56-cab999ccf59d
ms.openlocfilehash: 6ec12428b090d2317a6f2e5cc493d1e4f9392ff4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50494402"
---
# <a name="overview-of-windows-programming-in-c"></a>使用 C++ 設計 Windows 應用程式概觀

您可以使用 Visual c + + 撰寫許多種類的 (x x64 或 ARM），在 Windows 電腦上執行的程式，在雲端中，或在 Xbox 上的 Windows 伺服器上。 編寫完善的 c + + 程式會有這些品質：

- 有效率的記憶體需求
- 經濟實惠的功率耗用量
- 能夠充分利用多核心和多核心裝置
- 能夠進行一般運算圖形處理單元 (GPGPU)
- 能夠利用硬體中的其他方面近來的進步。

您可以使用 Visual C++ 開發數種廣泛的 Windows 應用程式分類。 這些分類有不同的程式設計模型或應用程式模型，採用了多年。 每一個模型使用不同的程式庫和 Api，來提供存取平台，並建立使用者介面，例如視窗和對話方塊。 C + + 標準程式庫，以及協力廠商程式庫可用在任何兩個類別，使用適用於 UWP 的一些限制。

- [Windows 通用應用程式](#BK_WindowsUniversal)。 Windows 應用程式的第三個分類在 Windows 8 中引入，並在 Windows 10 中繼續支援這類應用程式。 這些應用程式經常只稱為「Windows 應用程式」，而且其中包含以各種裝置為目標的桌上型電腦和行動應用程式。 您可以用 C++/CX 撰寫這些應用程式，這是包含 Windows 執行階段開發支援的 C++ 方言，或是使用標準 C++ 搭配使用 Windows 執行階段程式庫 (WRL) 的 COM 來撰寫。 這些應用程式原本專為全螢幕執行而設計，但是在 Windows 10 使用者可以選擇在桌面視窗中執行它們。 這些應用程式是觸控式導向，但如果使用者偏好的話，或是無法使用觸控式螢幕的情況，也很容易可用滑鼠來操作。 這些應用程式會從 Microsoft Store，因此它們被稱為 「 市集 」 應用程式散發。

UWP 應用程式就能夠執行所有的 Windows 10 裝置如平板電腦和行動電話上也能在桌面上執行。 在桌上型電腦，它們能夠以桌面視窗執行，而不是永遠以全螢幕方式執行。 在 Xbox 和未來的裝置上，也可以執行這些應用程式。  在 Windows 執行階段，可提供使用者介面項目、 服務和介面，以在 Windows 受支援之各種硬體裝置上，執行 UWP 應用程式。

您可以撰寫 UWP 應用程式，在 C + + /CX 中，與方言的 c + +，您可以使用[C + + /cli WinRT 程式庫](https://moderncpp.com/)在某些情況下。 UWP 應用程式編譯為原生程式碼並具有 XAML 使用者介面，或使用 DirectX。 以原生程式碼可以使用 以其他語言撰寫的 UWP 應用程式撰寫的 Windows 執行階段元件。 如需詳細資訊，請參閱 < [c + + 中建立通用 Windows 平台應用程式](http://go.microsoft.com/fwlink/?LinkID=534976)，[您第一個 UWP 使用 DirectX 建立遊戲](http://go.microsoft.com/fwlink/p/?LinkId=244656)，並[c + + 中的建立 Windows 執行階段元件](http://go.microsoft.com/fwlink/p/?LinkId=244658)。

   此分類也包括使用 C++ 處理核心元件和伺服器與雲端程式設計內容中的計算程式碼。 有時候伺服器或雲端應用程式核心的效能密集程式碼會以 C++ 撰寫，以使效能最大化。 您可以將這類程式碼編譯成 DLL，並從 C# 或 Visual Basic 使用它。

- **.NET Framework 應用程式**。 大部分的.NET Framework 應用程式以 C# 或 Visual Basic 撰寫，但是您也可以 C + + /cli CLI ( `/clr` Visual c + + 編譯器選項)。 我們建議針對包含 managed 和原生程式碼之較大型應用程式的最小 interop 圖層使用 C++/CLI。

##  <a name="BK_WindowsUniversal"></a> Windows Universal Apps

使用 Windows 10，應用程式能夠在所有 Windows 10 裝置如平板電腦和行動電話，以及在桌上型電腦上執行。 在桌上型電腦，它們能夠以桌面視窗執行，而不是永遠以全螢幕方式執行。 在 Xbox 和未來的裝置上，也可以執行這些應用程式。  兩種應用程式類型的程式設計模型與 Win32 桌面應用程式不同。 這些 Windows 應用程式是在 Windows 執行階段上執行，後者提供使用者介面項目、這些應用程式的基本服務，並提供與受支援之各種硬體裝置的介面。 這些應用程式編譯為原生程式碼，且具有 XAML 使用者介面，或使用 DirectX。 您也可以在其他 Windows 應用程式可以取用的原生程式碼中撰寫 Windows 執行階段元件，其中包括以 C#、 Visual Basic 或 JavaScript 所撰寫的應用程式。 如需詳細資訊，請參閱 < [c + + 中建立的 UWP"Hello world"應用程式](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)，[使用 DirectX 建立簡單的 UWP 遊戲](/windows/uwp/gaming/tutorial--create-your-first-uwp-directx-game)，並[c + + 中的建立 Windows 執行階段元件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)。

> [!TIP]
> 適用於 Windows 10 中，您可以使用 Desktop App Converter 來封裝現有傳統型應用程式透過 Microsoft Store 部署。 如需詳細資訊，請參閱 [Using Visual C++ Runtime in Centennial project](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project) (在 Centennial 專案中使用 Visual C++ 執行階段) 和[使用傳統型橋接器將您的傳統型應用程式移轉至通用 Windows 平台 (UWP)](https://msdn.microsoft.com/windows/uwp/porting/desktop-to-uwp-root)。

如需通用 Windows 平台範例，請參閱 [GitHub 上的 Windows 通用範例](https://github.com/Microsoft/Windows-universal-samples)

如果您有現有 Windows 8.1 專案，並想来移轉至 Windows 10，請參閱[移植到通用 Windows 平台](../porting/porting-to-the-universal-windows-platform-cpp.md)。 如果您有傳統 Win32 桌面程式庫和程式碼，您想要整合到 UWP 應用程式，請參閱[如何： 在通用 Windows 平台應用程式中使用現有 c + + Code](../porting/how-to-use-existing-cpp-code-in-a-universal-windows-platform-app.md)。

如需 UWP 的詳細資訊在一般情況下，請參閱[通用 Windows 平台 (UWP) 應用程式是什麼？](/windows/uwp/get-started/whats-a-uwp)。

如需所有這些概念的詳細資訊，請參閱 [Windows 通用應用程式指南](http://go.microsoft.com/fwlink/p/?linkid=534605)。

##  <a name="BK_Native"></a> 桌面和伺服器應用程式

若要了解為桌上型電腦撰寫 Windows 用戶端應用程式的基本概念，請參閱 [Developing Windows Applications in C++](https://msdn.microsoft.com/vstudio//hh304489) (使用 C++ 開發 Windows 應用程式) 和 [Introduction to Windows Programming in C++](https://msdn.microsoft.com/library/windows/desktop/ff381398)(使用 C++ 進行 Windows 程式設計的簡介)。

在 Windows 10 中，您可以使用 Visual c + + 建立各式各樣的桌面程式：

- 命令列應用程式和公用程式。 如需詳細資訊，請參閱 <<c0> [ 主控台應用程式](../windows/console-applications-in-visual-cpp.md)。

- 具有複雜圖形使用者介面的消費者應用程式。 如需詳細資訊，請參閱 [Hilo: Developing C++ Applications for Windows](http://go.microsoft.com/fwlink/p/?LinkId=256417)(Hilo：為 Windows 開發 C++ 應用程式)

- 企業和營運的.NET Framework 上執行的應用程式。 大部分的.NET Framework 應用程式是以 C# 或 Visual Basic 撰寫的。 您可以使用 C + + /cli CLI 來建立可讓.NET 程式碼使用原生 c + + 程式庫的 interop 圖層。 如需詳細資訊，請參閱 < [.NET 程式設計使用 C + + /cli （Visual c + +）](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)。

- 以機器碼執行的 SQL 資料庫用戶端。 如需詳細資訊，請參閱 [SQL Server Native Client](/sql/relational-databases/native-client/odbc/sql-server-native-client-odbc)。

- Microsoft Office 應用程式的增益集。 如需詳細資訊，請參閱 [Building a C++ Add-in for Outlook 2010](http://go.microsoft.com/fwlink/p/?LinkId=256420)(建置 Outlook 2010 的 C++ 增益集)

- 裝置驅動程式。 如需詳細資訊，請參閱 [Windows 驅動程式套件 (WDK)](http://go.microsoft.com/fwlink/p/?LinkId=256421)

- Windows 服務 如需詳細資訊，請參閱 [Introduction to Windows Service Applications](/dotnet/framework/windows-services/introduction-to-windows-service-applications)。

您可以使用 Visual C++ 將幾乎任何類型的自訂高效能功能包裝成 Win32 DLL，或可由 C++ 應用程式或以其他語言 (例如 C# 或 Visual Basic) 所撰寫的應用程式使用的 COM DLL。 如需 WIn32 DLL 的詳細資訊，請參閱 [DLLs in Visual C++](../build/dlls-in-visual-cpp.md)。 如需開發 COM 的詳細資訊，請參閱 [Component Object Model (COM)](/windows/desktop/com/component-object-model--com--portal)。

## <a name="games"></a>遊戲

DirectX 遊戲可以在 PC 或 Xbox 上執行。 如需詳細資訊，請參閱 [DirectX 開發人員中心](http://go.microsoft.com/fwlink/p/?LinkId=256418)。

## <a name="sdks-libraries-and-header-files"></a>Sdk、 程式庫和標頭檔

Visual c + + 包含 C 執行階段程式庫 (CRT)、 c + + 標準程式庫和其他 Microsoft 特定程式庫。 包含這些程式庫標頭檔的 include 資料夾位於在 Visual Studio 安裝目錄下的 \VC\ 資料夾中，或在 CRT，在 Windows SDK 安裝資料夾的情況下。

您可以使用[Vcpkg 套件管理員](../vcpkg.md)方便的 Windows 中安裝數百個第三方開放原始碼程式庫。

Microsoft 程式庫包括：

- Microsoft Foundation Classes (MFC)：一種物件導向架構，用於建立具有豐富使用者介面 (例如按鈕、清單方塊、樹狀檢視和其他控制項) 的傳統 Windows 程式 (特別是企業應用程式)。 如需詳細資訊，請參閱 [MFC Desktop Applications](../mfc/mfc-desktop-applications.md)。

- Active Template Library (ATL)：用於建立 COM 元件的強大協助程式庫。 如需詳細資訊，請參閱 [ATL COM Desktop Components](../atl/atl-com-desktop-components.md)。

- C++ AMP (C++ Accelerated Massive Parallelism)：可讓您在 GPU 上執行高效能通用計算工作的程式庫。 如需詳細資訊，請參閱 [C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)。

- 並行執行階段：可簡化多核心 (multicore) 和數個核心 (many-core) 裝置的平行和非同步程式設計工作的程式庫。 如需詳細資訊，請參閱 [Concurrency Runtime](../parallel/concrt/concurrency-runtime.md)。

許多 Windows 程式設計案例也需要使用 Windows SDK，它包含了可讓您存取 Windows 作業系統元件的標頭檔。 根據預設，Visual Studio 會安裝 Windows SDK 的 c + + 桌面工作負載，讓您能夠開發通用 Windows 應用程式的元件。 若要開發 UWP 應用程式，您需要 Windows 10 的 Windows SDK 版本。 如需資訊，請參閱[Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk)。 (如需舊版 Windows 的 Windows Sdk 的詳細資訊，請參閱[Windows SDK 封存](https://developer.microsoft.com/windows/downloads/sdk-archive))。

**程式檔案 (x86) \Windows 套件**是您已安裝的 Windows sdk 的所有版本的預設位置。

其他平台 (例如 Xbox 和 Azure) 有它們自己的 SDK，您可能必須安裝這些 SDK。 如需詳細資訊，請參閱 DirectX 開發人員中心和 Azure 開發人員中心。

## <a name="development-tools"></a>開發工具

Visual Studio 含有功能強大的機器碼偵錯工具、靜態分析工具、圖形偵錯工具、全功能的程式碼編輯器、單元測試支援，以及許多其他工具和公用程式。 如需詳細資訊，請參閱 <<c0> [ 開始使用 Visual Studio 進行開發](/visualstudio/ide/get-started-developing-with-visual-studio)，並[IDE 和開發工具](../ide/ide-and-tools-for-visual-cpp-development.md)。

## <a name="related-articles"></a>相關文章

|標題|描述|
|-----------|-----------------|
|[Visual C++](../visual-cpp-in-visual-studio.md)|Visual c + + 開發人員內容的父主題。|
