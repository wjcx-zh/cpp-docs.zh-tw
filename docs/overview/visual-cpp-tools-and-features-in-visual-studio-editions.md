---
title: Visual Studio 版本中的 C++ 工具和功能
ms.date: 05/21/2019
helpviewer_keywords:
- tools and platforms [C++]
ms.assetid: 3d88607b-9cc4-490a-8d4c-31ee7610a26f
ms.openlocfilehash: 03a28c87bd0a122229a7e93b7077b1d6e3fea53f
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079246"
---
# <a name="c-tools-and-features-in-visual-studio-editions"></a>Visual Studio 版本中的 C++ 工具和功能

::: moniker range=">=vs-2019"

Visual Studio 2019 中提供下列 C++ 功能。 除非另有指示，否則所有版本都可使用所有的功能： Visual Studio Community、Visual Studio Professional 和 Visual Studio Enterprise。 有些功能需要特定的工作負載或選擇性元件，您可以使用 Visual Studio 安裝程式來安裝它們。

## <a name="platforms"></a>平台

- Windows 桌面
- 通用 Windows 平台 ((平板電腦、電腦、Xbox、IoT 和 HoloLens))
- Linux
- Android
- iOS

## <a name="compilers"></a>編譯器

- 適用於 x86、x64、ARM 及 ARM64 的 MSVC 32 位元編譯器
- 適用於 x86、x64、ARM 及 ARM64 的 MSVC 64 位元編譯器
- ARM 的 GCC 跨編譯器
- Clang/LLVM
  - 在 Windows 上，Clang/LLVM 7.0，目標設為 x86 或 x64 (僅限 CMake 支援)。 其他 Clang 版本可能會運作，但未正式支援。
  - 在 Linux 上，散發版本支援的任何 Clang/LLVM 安裝。

## <a name="c-workloads"></a>C++ 工作負載

Visual Studio 包含下列工作負載以進行 C++ 開發。 您可以安裝這些項目的任何一個或全部，以及其他工作負載，例如 .NET 桌面開發、Python 開發、Azure 開發、Visual Studio 延伸模組開發和其他項目。

### <a name="desktop-development-with-c"></a>使用 C++ 的桌面開發

包含：
- C++ 核心桌面功能

選擇性元件：
- MSVC v142 - VS 2019 C++ x64/x86 建置工具 (v14.21)
- Windows 10 SDK (10.0.17763.0)
- Just-in-Time 偵錯工具
- C++ 分析工具
- 適用於 Windows 的 C++ CMake 工具
- 適用於 v142 建置工具的 C++ ALT (x86 & x64)
- Boost.Test 的測試配接器
- 適用於 Google Test 的測試配接器
- Live Share
- IntelliCode
- IntelliTrace (僅限 Enterprise)
- 適用於 v142 建置工具的 C++ MFC (x86 & x64)
- 適用於 v142 建置工具的 C++/CLI 支援 (14.21)
- 適用於 v142 建置工具的 C++ 模組 (x64/x86 – 實驗性)
- 適用於 Windows 的 Clang 編譯器
- IncrediBuild - 組建加速
- Windows 10 SDK (10.0.17134.0)
- Windows 10 SDK (10.0.16299.0)
- MSVC v141 - VS 2017 C++ x64/x86 建置工具 (v14.16)
- MSVC v140 - VS 2015 C++ 建置工具 (v14.00)

### <a name="linux-development-with-c"></a>使用 C++ 的 Linux 程式開發

包含：
- C++ 核心功能
- Windows 通用 C 執行階段
- 適用於 Linux 開發的 C++

選擇性元件：
- 適用於 Linux 的 C++ CMake 工具
- 內嵌與 IoT 開發工具

### <a name="universal-windows-platform-development"></a>通用 Windows 平台開發

包含：
- Blend for Visual Studio
- .NET Native 和.NET Standard
- NuGet 套件管理員
- 通用 Windows 平台工具
- Windows 10 SDK (10.0.17763.0)

選擇性元件：
- IntelliCode
- IntelliTrace (僅限 Enterprise)
- USB 裝置連線
- C++ (v142) 通用 Windows 平台工具
- C++ (v141) 通用 Windows 平台工具
- 適用於 DirectX 的圖形偵錯工具與 GPU 分析工具
- Windows 10 SDK (10.0.18362.0)
- Windows 10 SDK (10.0.17134.0)
- Windows 10 SDK (10.0.16299.0)
- 架構與分析工具

### <a name="c-game-development"></a>C++ 遊戲開發

包含：
- C++ 核心功能
- Windows 通用 C 執行階段
- C++ 2019 可轉散發更新
- MSVC v142 - VS 2019 C++ x64/x86 建置工具 (v14.21)

選擇性元件：
- C++ 分析工具
- Windows 10 SDK (10.0.17763.0)
- IntelliCode
- IntelliTrace (僅限 Enterprise)
- Windows 10 SDK (10.0.17134.0)
- Windows 10 SDK (10.0.16299.0)
- IncrediBuild - 組建加速
- Cocos
- Unreal Engine 安裝程式
- Unreal 引擎的 Android IDE 支援

### <a name="mobile-development-with-c"></a>使用 C++ 進行行動裝置開發

包含：
- C++ 核心功能
- Android SDK 安裝程式 (API 層級 25) (可用於以 C++ 進行行動裝置開發的本機安裝)

選擇性元件：
- Android NDK (R16B)
- Apache Ant (1.9.3)
- C++ Android 開發工具
- IntelliCode
- Google Android 模擬器 (API 層級 25) (本機安裝)
- Intel Hardware Accelerated Execution Manager (HAXM) (本機安裝)
- Android NDK (R16B) (32 位元)
- C++ iOS 開發工具
- IncrediBuild - 組建加速

## <a name="individual-components"></a>個別元件

您可以從任何工作負載獨立安裝這些元件。

- JavaScript 診斷
- Live Share
- 適用於 v142 建置工具的 C++ 通用 Windows 平台執行階段
- ClickOnce 發行
- Microsoft Visual Studio 安裝程式專案

## <a name="libraries-and-headers"></a>程式庫和標頭

- Windows 標頭和程式庫
- Windows 通用 C 執行階段 (CRT)
- C++ 標準程式庫
- ATL
- MFC
- .NET Framework 類別庫
- 適用於 .NET 的 C++ 支援程式庫
- OpenMP 2.0
- 900 個以上透過 vcpkg 目錄的開放原始碼程式庫

## <a name="build-and-project-systems"></a>建置和專案系統

- CMake
- 透過開啟資料夾的任何建置系統
- 命令列組建 (msbuild.exe)
- 原生多目標
- Managed 多目標
- 平行組建
- 組建自訂
- 屬性頁擴充性

## <a name="project-templates"></a>專案範本

根據您已安裝哪些工作負載，可以使用下列專案範本。

Windows 桌面：
- 空專案
- 主控台應用程式
- Windows 傳統式精靈
- Windows 傳統型應用程式
- 共用的項目專案
- MFC 應用程式
- 動態連結程式庫
- CLR 空專案
- CLR 主控台應用程式
- 靜態程式庫
- CMake 專案
- ATL 專案
- MFC 動態連結程式庫
- CLR 類別庫
- Makefile 專案 (Windows)
- MFC ActiveXControl
- 原生單元測試專案
- Google Test

通用 Windows 平台 (C++/CX)：
- 空白應用程式
- DirectX 11 和 XAML 應用程式
- DirectX 11 應用程式
- DirectX 12 應用程式
- 單元測試應用程式
- DLL
- Windows Runtime 元件
- 靜態程式庫
- Windows 應用程式封裝專案

Linux：
- 主控台應用程式 (Linux)
- 空專案 (Linux)
- Raspberry Pi Blink
- Makefile 專案 (Linux)

## <a name="tools"></a>工具

- Incremental 連結器 (Link.exe)
- Microsoft Makefile 公用程式 (Nmake.exe)
- 程式庫產生器 (Lib.exe)
- Windows 資源編譯器 (Rc.exe)
- Windows Resource to Object Converter (CvtRes.exe)
- Browse Information Maintenance Utility (BscMake.exe)
- C++ 名稱 Undecorator (Undname.exe)
- COFF/PE 傾印工具 (Dumpbin.exe)
- COFF/PE 編輯器 (Editbin.exe)
- MASM (Ml.exe)
- Spy++
- ErrLook
- AtlTrace
- 推斷規則
- 特性指引最佳化

## <a name="debugging-features"></a>偵錯功能

- 機器碼偵錯
- natvis (原生類型視覺效果)
- 圖形偵錯
- Managed 偵錯
- GPU 使用量
- 記憶體使用量
- 遠端偵錯
- SQL 偵錯
- 靜態程式碼分析

## <a name="designers-and-editors"></a>設計工具和編輯器

- XAML 設計工具
- CSS 樣式設計工具/編輯器
- HTML 設計工具/編輯器
- XML 編輯器
- 原始程式碼編輯器
- 生產力功能：重構、EDG IntelliSense 引擎、 C++程式碼格式
- Windows Form 設計工具
- 資料設計工具
- 原生資源編輯器 (.rc 檔)
- 資源編輯器
- 模型編輯器
- 著色器設計工具
- 即時相依性驗證 (僅限 Enterprise)
- 架構分層圖 (僅限 Enterprise)
- 架構驗證 (僅限 Enterprise)
- 程式碼複製品 (僅限 Enterprise)

## <a name="data-features"></a>資料功能

- 資料設計工具
- 資料物件
- Web 服務
- Server Explorer

## <a name="automation-and-extensibility"></a>Automation 與擴充性

- 擴充性物件模型
- 程式碼模型
- 專案模型
- 資源編輯器模型
- 精靈模型
- 偵錯工具物件模型

## <a name="application-lifecycle-management-tools"></a>應用程式生命週期管理工具

- 單元測試 (Microsoft 原生 C++、Boost.Test、Google Test、CTest)
- Code Map 和相依性關係圖 (Professional 和 Enterprise)
- 程式碼涵蓋範圍 (僅限 Enterprise)
- 手動測試 (僅限 Enterprise)
- 探勘測試 (僅限 Enterprise)
- 測試案例管理 (僅限 Enterprise)
- Code Map 偵錯工具整合 (僅限 Enterprise)
- 即時單元測試 (僅限 Enterprise)
- IntelliTrace (僅限 Enterprise)
- IntelliTest (僅限 Enterprise)
- Microsoft Fakes (單元測試隔離) (僅限 Enterprise)
- 程式碼涵蓋範圍 (僅限 Enterprise)

## <a name="see-also"></a>另請參閱

[安裝 Visual Studio](/visualstudio/install/install-visual-studio)<br/>
[Visual Studio 的新功能](/visualstudio/ide/whats-new-in-visual-studio)<br/>
[Visual Studio 中的 C++ 專案類型](../build/reference/visual-cpp-project-types.md)

::: moniker-end

::: moniker range="<=vs-2017"

下表顯示 Visual Studio 2017 中可用的 Visual C++ 功能。 儲存格中的 X 表示功能可用；空白儲存格表示功能不可用。 括號括住的附註表示功能可用，但有所限制。

## <a name="platforms"></a>平台

||||||
|-|-|-|-|-|
|平台|Visual Studio Express for Windows 10|Visual Studio Express for Windows Desktop|Visual Studio Community/Professional|Visual Studio Enterprise|
|Windows 桌面||X|X|X|
|通用 Windows 平台 ((電話、平板電腦、電腦、Xbox、IoT 和 HoloLens))|X||X|X|
|Linux|X|X|
|Microsoft Store 8.1|||X|X|
|Windows Phone 8.0|||X|X|
|Android|||X|X|
|iOS|||X|X|

## <a name="compilers"></a>編譯器

|編譯器|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|--------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|MSVC 32 位元 x86 編譯器|X|X|X|X|
|X86_arm 跨平台編譯器|X||X|X|
|MSVC 64 位元 x64 編譯器|||X|X|
|X86_ x64 跨平台編譯器|X|X|X|X|

## <a name="libraries-and-headers"></a>程式庫和標頭

|程式庫或標頭|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|-----------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Windows 標頭及程式庫和 CRT 程式庫|(X)|X|X|X|
|C++ 標準程式庫|X|X|X|X|
|ATL|||X|X|
|MFC|||X|X|
|.NET Framework 類別庫||X|X|X|
|適用於 .NET 的 C++ 支援程式庫||X|X|X|
|OpenMP 2.0|X|X|X|X|

## <a name="project-templates"></a>專案範本

|[範本]|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|--------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|UWP、Windows 8.1、Windows Phone 8.0 的 XAML 範本|X||X|X|
|Direct3D 應用程式|X||X|X|
|DLL (通用 Windows)|X||X|X|
|靜態程式庫 (通用 Windows)|X||X|X|
|Windows Runtime 元件|X||X|X|
|單元測試應用程式 (通用 Windows)|X||X|X|
|ATL 專案|||X|X|
|類別庫 (CLR)||X|X|X|
|CLR 主控台應用程式||X|X|X|
|CLR 空專案||X|X|X|
|自訂精靈|||X|X|
|空專案||X|X|X|
|Makefile 專案||X|X|X|
|MFC ActiveX 控制項|||X|X|
|MFC 應用程式|||X|X|
|MFC DLL|||X|X|
|測試專案|X|X|X|X|
|Win32 主控台應用程式||X|X|X|
|Win32 專案||X|X|X|

## <a name="tools"></a>工具

|工具|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|----------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Incremental 連結器 (Link.exe)|X|X|X|X|
|Program Maintenance Utility (Nmake.exe)||X|X|X|
|程式庫產生器 (Lib.exe)|X|X|X|X|
|Windows 資源編譯器 (Rc.exe)|X|X|X|X|
|Windows Resource to Object Converter (CvtRes.exe)||X|X|X|
|Browse Information Maintenance Utility (BscMake.exe)|X|X|X|X|
|C++ 名稱 Undecorator (Undname.exe)|X|X|X|X|
|COFF/PE 傾印工具 (Dumpbin.exe)|X|X|X|X|
|COFF/PE 編輯器 (Editbin.exe)|X|X|X|X|
|MASM (Ml.exe)|||X|X|
|Spy++|||X|X|
|ErrLook|||X|X|
|AtlTrace|||X|X|
|Devenv.com|||X|X|
|推斷規則|||X|X|
|將 VCBuild.vcproj 專案升級為 MSBuild (VCUpgrade.exe)|X|X|X|X|
|特性指引最佳化|||X|X|

## <a name="debugging-features"></a>偵錯功能

|偵錯功能|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|-----------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|機器碼偵錯|X|X|X|X|
|natvis (原生類型視覺效果)|X|X|X|X|
|圖形偵錯|X||X|X|
|Managed 偵錯||X|X|X|
|GPU 使用量|X||X|X|
|記憶體使用量|X||X|X|
|遠端偵錯|X|X|X|X|
|SQL 偵錯|||X|X|
|靜態程式碼分析|限制|限制|X|X|

## <a name="designers-and-editors"></a>設計工具和編輯器

|設計工具或編輯器|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|XAML 設計工具|X||X|X|
|CSS 樣式設計工具/編輯器|X|X|X|X|
|HTML 設計工具/編輯器|X|X|X|X|
|XML 編輯器|X|X|X|X|
|原始程式碼編輯器|X|X|X|X|
|產能功能：重構、IntelliSense、C++ 程式碼格式化|X|X|X|X|
|Windows Form 設計工具||X|X|X|
|資料設計工具|||X|X|
|原生資源編輯器 (.rc 檔)|||X|X|
|資源編輯器|X|X|X|X|
|模型編輯器|X||X|X|
|著色器設計工具|X||X|X|

## <a name="data-features"></a>資料功能

|資料功能|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|資料設計工具|||X|X|
|資料物件|||X|X|
|Web 服務|||X|X|
|Server Explorer|||X|X|

## <a name="build-and-project-systems"></a>建置和專案系統

|建置或專案功能|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|------------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|命令列組建 (msbuild.exe)|X|X|X|X|
|原生多目標||X|X|X|
|Managed 多目標||X|X|X|
|平行組建|X|X|X|X|
|組建自訂|X|X|X|X|
|屬性頁擴充性|X|X|X|X|

## <a name="automation-and-extensibility"></a>Automation 與擴充性

|Automation 與擴充性|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|----------------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|擴充性物件模型|||X|X|
|程式碼模型|||X|X|
|專案模型|||X|X|
|資源編輯器模型|||X|X|
|精靈模型|||X|X|
|偵錯工具物件模型|||X|X|

## <a name="application-lifecycle-management-tools"></a>應用程式生命週期管理工具

||||||
|-|-|-|-|-|
|工具|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|單元測試 (原生架構)|X|X|X|X|
|單元測試 (Managed 架構)||X|X|X|
|程式碼涵蓋範圍||||X|
|手動測試||||X|
|探勘測試||||X|
|測試案例管理||||X|
|程式碼對應和相依性圖形|||唯讀|X|
|程式碼對應偵錯||||X|

## <a name="see-also"></a>另請參閱

[安裝 Visual Studio](/visualstudio/install/install-visual-studio)<br/>
[Visual Studio 的新功能](/visualstudio/ide/whats-new-in-visual-studio)<br/>
[Visual Studio 中的 C++ 專案類型](../build/reference/visual-cpp-project-types.md)

::: moniker-end
