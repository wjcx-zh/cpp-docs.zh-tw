---
title: "使用 C++ 設計 Windows 應用程式概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: efc691d7-21f3-47ae-ae56-cab999ccf59d
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用 C++ 設計 Windows 應用程式概觀
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以使用 Visual C\+\+ 來撰寫可在 Windows 電腦上 \(x86、x64 或 ARM\)、在 Windows Server 上、在雲端，或者在 Xbox 上執行的各種程式。 編寫完善的 C\+\+ 程式是快速的、有效率的、省電的，並且能夠有效利用多核心 \(multicore\) 和數個核心 \(many\-core\) 的裝置、圖形處理單元 \(GPGPU\) 的通用計算以及其他最新的硬體。  
  
 您可以使用 Visual C\+\+ 開發數種廣泛的 Windows 應用程式分類。 這些分類有不同的程式設計模型或應用程式模型，也就是說它們使用不同的程式庫和 API，提供平台存取和使用者介面。  
  
-   [Windows 通用應用程式](#BK_WindowsUniversal)。 Windows 應用程式的第三個分類在 Windows 8 中引入，並在 Windows 10 中繼續支援這類應用程式。 這些應用程式經常只稱為「Windows 應用程式」，而且其中包含以各種裝置為目標的桌上型電腦和行動應用程式。 您可以用 C\+\+\/CX 撰寫這些應用程式，這是包含 Windows 執行階段開發支援的 C\+\+ 方言，或是使用標準 C\+\+ 搭配使用 Windows 執行階段程式庫 \(WRL\) 的 COM 來撰寫。 這些應用程式原本專為全螢幕執行而設計，但是在 Windows 10 使用者可以選擇在桌面視窗中執行它們。 這些應用程式是觸控式導向，但如果使用者偏好的話，或是無法使用觸控式螢幕的情況，也很容易可用滑鼠來操作。 這些應用程式從 Windows 市集散發，因此它們被稱為「Windows 市集應用程式」。  
  
-   [桌面、伺服器和雲端應用程式與遊戲](#BK_Native)。 這個分類包括 Windows 桌面應用程式，有時也稱為 Win32 應用程式，因為這些應用程式在 Windows 8 之前使用 Win32 API，所有的 Windows 應用程式過去都在此分類中。 此分類中的應用程式可以使用 MFC 處理使用者介面，使用 ATL 與 Windows 元件 \(通常是 COM 物件\) 進行互動。  
  
     使用標準 C\+\+ 撰寫的應用程式、元件或程式庫也屬於此分類。  
  
     此分類也包括使用 C\+\+ 處理核心元件和伺服器與雲端程式設計內容中的計算程式碼。 有時候伺服器或雲端應用程式核心的效能密集程式碼會以 C\+\+ 撰寫，以使效能最大化。 您可以將這類程式碼編譯成 DLL，並從 C\# 或 Visual Basic 使用它。  
  
-   **.NET Framework 應用程式**。 大部分的 .NET Framework 應用程式以 C\# 或 Visual Basic 撰寫，但是您也可以 C\+\+\/CLI \(Visual C\+\+ 中的 \/clr 編譯器選項\)。 我們建議針對包含 managed 和原生程式碼之較大型應用程式的最小 interop 圖層使用 C\+\+\/CLI。  
  
##  <a name="BK_WindowsUniversal"></a> Windows 通用應用程式  
 使用 Windows 10，應用程式能夠在所有 Windows 10 裝置如平板電腦和行動電話，以及在桌上型電腦上執行。 在桌上型電腦，它們能夠以桌面視窗執行，而不是永遠以全螢幕方式執行。 在 Xbox 和未來的裝置上，也可以執行這些應用程式。  兩種應用程式類型的程式設計模型與 Win32 桌面應用程式不同。 這些 Windows 應用程式是在 Windows 執行階段上執行，後者提供使用者介面項目、這些應用程式的基本服務，並提供與受支援之各種硬體裝置的介面。 這些應用程式編譯為原生程式碼，且具有 XAML 使用者介面，或使用 DirectX。 您也可以用機器碼撰寫 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 元件讓其他 Windows 應用程式 \(包括以 C\#、Visual Basic 或 JavaScript 所撰寫的應用程式\) 能夠使用。 如需詳細資訊，請參閱[使用 C\+\+ 建立您的第一個 Windows 市集應用程式](http://go.microsoft.com/fwlink/?LinkID=534976)、[使用 DirectX 建立您的第一個 Windows 市集遊戲](http://go.microsoft.com/fwlink/p/?LinkId=244656)及[在 C\+\+ 中建立 Windows 執行階段元件](http://go.microsoft.com/fwlink/p/?LinkId=244658)。  
  
 如需通用 Windows 平台範例，請參閱 [GitHub 上的 Windows 通用範例](https://github.com/Microsoft/Windows-universal-samples)  
  
 若您有 Windows 8.1 專案，並想將其移轉至 Windows 10，請參閱[移植到通用 Windows 平台](../porting/porting-to-the-universal-windows-platform-cpp.md)。 若您有傳統 Win32 桌面程式庫及程式碼，並想要整合到 UWP 應用程式，請參閱[做法：在通用 Windows 平台應用程式中使用現有的 C\+\+ 程式碼](../porting/how-to-use-existing-cpp-code-in-a-universal-windows-platform-app.md)。  
  
 您也可以撰寫通用 Windows 應用程式、遊戲和元件，而不需要使用 [!INCLUDE[cppwrt](../build/reference/includes/cppwrt_md.md)] \([!INCLUDE[cppwrt_short](../build/reference/includes/cppwrt_short_md.md)]\)；您可以改為使用 [!INCLUDE[cppwrl](../windows/includes/cppwrl_md.md)] \([!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)]\)。 如需詳細資訊，請參閱[Windows Runtime C\+\+ Template Library \(WRL\)](../windows/windows-runtime-cpp-template-library-wrl.md)。  
  
 使用 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)]，您可以開發在 Windows 10 桌上型電腦和行動裝置上執行的通用 Windows 應用程式。 您也可以在 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 中開發 Windows 8.1 應用程式和 Windows Phone 8.1 應用程式，但是要這樣做，必須先在相同電腦上安裝 Visual Studio 2013，然後設定您的專案使用 **Visual Studio 2013 \(v120\)** 工具組。 若要在您的專案中進行此設定，請開啟專案的屬性，並在 \[一般\] 區段中，將 \[平台工具組\] 設為 \[Visual Studio 2013 \(v120\)\]。  
  
 如果您在 Visual Studio 安裝程式中安裝 Phone 8.0 工具，您也可以針對 Windows Phone 8.0。  
  
 Windows 10 中引進了一個新概念稱為 API 合約，它會取代以特定 Windows 版本為目標的舊作法。 相反地，您可以選擇您的應用程式需求哪些 API 合約，它便會在支援這些合約的任何 Windows 裝置上執行。 API 合約是一組穩定的 API，提供平台或裝置資源的存取權。 API 合約可以包含做為專案系統中的參考。 在 Visual Studio 專案中，如果您加入對特定擴充功能 SDK 的參考，Visual Studio 便會加入適當的 API 合約。  
  
 如需所有這些概念的詳細資訊，請參閱 [Windows 通用應用程式指南](http://go.microsoft.com/fwlink/?LinkId=534605)。  
  
##  <a name="BK_Win32"></a> 桌面、伺服器和雲端應用程式與遊戲  
 在雲端中，您可以使用 C\+\+ 撰寫 Azure 機器碼組件，然後從以 C\# 建立的 Web 角色來呼叫它們。 如需詳細資訊，請參閱 [Azure SDK](http://go.microsoft.com/fwlink/p/?LinkId=256416)。  
  
 若要了解為桌上型電腦撰寫 Windows 用戶端應用程式的基本概念，請參閱 [Developing Windows Applications in C\+\+](http://msdn.microsoft.com/vstudio//hh304489) \(使用 C\+\+ 開發 Windows 應用程式\) 和 [Introduction to Windows Programming in C\+\+](http://msdn.microsoft.com/library/windows/desktop/ff381398\(v=vs.85\).aspx) \(使用 C\+\+ 進行 Windows 程式設計的簡介\)。  
  
 在 Windows 10 上，您可以使用 Visual C\+\+ 建立各式各樣的程式：  
  
-   命令列應用程式和公用程式。 如需詳細資訊，請參閱[主控台應用程式](../windows/console-applications-in-visual-cpp.md)。  
  
-   在電腦或 Xbox 上執行的 DirectX 遊戲。 如需詳細資訊，請參閱 [DirectX 開發人員中心](http://go.microsoft.com/fwlink/p/?LinkId=256418)。  
  
-   具有複雜圖形使用者介面的消費者應用程式。 如需詳細資訊，請參閱 [Hilo: Developing C\+\+ Applications for Windows](http://go.microsoft.com/fwlink/p/?LinkId=256417) \(Hilo：為 Windows 開發 C\+\+ 應用程式\)  
  
-   在 .NET Framework 上執行的企業和營運應用程式，或做為 .NET Framework 應用程式和以機器碼撰寫的應用程式或元件之間的橋接功能的應用程式。 如需詳細資訊，請參閱[以 C\+\+\/CLI 進行 .NET 程式設計](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)。  
  
-   以機器碼執行的 SQL 資料庫用戶端。 如需詳細資訊，請參閱 [SQL Server Native Client](http://go.microsoft.com/fwlink/p/?LinkId=256419)。  
  
-   Microsoft Office 應用程式的增益集。 如需詳細資訊，請參閱 [Building a C\+\+ Add\-in for Outlook 2010](http://go.microsoft.com/fwlink/p/?LinkId=256420) \(建置 Outlook 2010 的 C\+\+ 增益集\)  
  
-   裝置驅動程式。 如需詳細資訊，請參閱 [Windows 驅動程式套件 \(WDK\)](http://go.microsoft.com/fwlink/p/?LinkId=256421)  
  
-   Windows 服務 如需詳細資訊，請參閱[Windows 服務應用程式簡介](../Topic/Introduction%20to%20Windows%20Service%20Applications.md)。  
  
 您可以使用 Visual C\+\+ 將幾乎任何類型的自訂高效能功能包裝成 Win32 DLL，或可由 C\+\+ 應用程式或以其他語言 \(例如 C\# 或 Visual Basic\) 所撰寫的應用程式使用的 COM DLL。 如需 WIn32 DLL 的詳細資訊，請參閱 [Visual C\+\+ 中的 DLL](../build/dlls-in-visual-cpp.md)。 如需開發 COM 的詳細資訊，請參閱 [Component Object Model \(COM\)](http://msdn.microsoft.com/zh-tw/375d29a7-a1f3-4bd8-8621-bad7a049b2aa)。  
  
## SDK 及標頭檔  
 Visual C\+\+ 包含 C 和 C\+\+ 標準程式庫、標準範本庫 \(STL\) 以及其他 Microsoft 特定程式庫。 包含這些程式庫之標頭檔的 Include 資料夾，位於 Visual Studio 安裝目錄的 \\VC\\ 資料夾下，或是在 C Runtime \(CRT\) 程式庫的情況下則位於 Windows SDK 安裝資料夾，例如在您 Windows 10 SDK 的 Program Files 資料夾下的 Windows Kits\\10。  Microsoft 程式庫包括：  
  
-   Microsoft Foundation Classes \(MFC\)：一種物件導向架構，用於建立具有豐富使用者介面 \(例如按鈕、清單方塊、樹狀檢視和其他控制項\) 的傳統 Windows 程式 \(特別是企業應用程式\)。 如需詳細資訊，請參閱[MFC 桌面應用程式](../mfc/mfc-desktop-applications.md)。  
  
-   Active Template Library \(ATL\)：用於建立 COM 元件的強大協助程式庫。 如需詳細資訊，請參閱[ATL COM Desktop Components](../atl/atl-com-desktop-components.md)。  
  
-   C\+\+ AMP \(C\+\+ Accelerated Massive Parallelism\)：可讓您在 GPU 上執行高效能通用計算工作的程式庫。 如需詳細資訊，請參閱[C\+\+ AMP \(C\+\+ Accelerated Massive Parallelism\)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)。  
  
-   並行執行階段：可簡化多核心 \(multicore\) 和數個核心 \(many\-core\) 裝置的平行和非同步程式設計工作的程式庫。 如需詳細資訊，請參閱[並行執行階段](../parallel/concrt/concurrency-runtime.md)。  
  
 許多 Windows 程式設計案例也需要使用 Windows SDK，它包含了可讓您存取 Windows 作業系統元件的標頭檔。 根據預設，[!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)] 的所有版本都會安裝 Windows SDK，讓您能夠開發通用 Windows 應用程式。 若要開發 Windows 10 的通用 Windows 應用程式，您需要 Windows 10 版本的 Windows SDK。 如需 Windows 10 SDK 的資訊，請參閱 [Windows 10 SDK](http://go.microsoft.com/fwlink/p/?LinkId=534603) \(如需舊版 Windows 之 Windows SDK 的詳細資訊，請參閱 [Windows SDK 概觀](../Topic/Overview%20of%20the%20Windows%20SDK.md)\)。  
  
 其他平台 \(例如 Xbox 和 Azure\) 有它們自己的 SDK，您可能必須安裝這些 SDK。 如需詳細資訊，請參閱 DirectX 開發人員中心和 Azure 開發人員中心。  
  
## 開發工具  
 Visual Studio 含有功能強大的機器碼偵錯工具、靜態分析工具、圖形偵錯工具、全功能的程式碼編輯器、單元測試支援，以及許多其他工具和公用程式。 如需詳細資訊，請參閱 [Visual Studio 應用程式開發](http://msdn.microsoft.com/zh-tw/97490c1b-a247-41fb-8f2c-bc4c201eff68)和 [IDE 和開發工具](../ide/ide-and-tools-for-visual-cpp-development.md)。  
  
## 相關文章  
  
|標題|描述|  
|--------|--------|  
|[Visual C\+\+](../top/visual-cpp-in-visual-studio-2015.md)|MSDN Library 有關 C\+\+ 內容的父主題。|