---
title: 教學課程： vcperf 和 Windows Performance Analyzer
description: 如何使用 vcperf 和 WPA 來分析 c + + 組建追蹤的教學課程。
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b82c1f7105b3fd03d8c21dd79617dbc66f3e090c
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507775"
---
# <a name="tutorial-vcperf-and-windows-performance-analyzer"></a>教學課程： vcperf 和 Windows Performance Analyzer

::: moniker range="<=vs-2017"

C + + Build Insights 工具可在 Visual Studio 2019 中取得。 若要查看此版本的檔，請將此文章的 Visual Studio **版本** 選取器控制項設定為 Visual Studio 2019。 您可在此頁面的目錄頂端找到此檔案。

::: moniker-end
::: moniker range="vs-2019"

在本教學課程中，您將瞭解如何使用 *vcperf.exe* 來收集 c + + 組建的追蹤。 您也將瞭解如何在 Windows Performance Analyzer 中查看這項追蹤。

## <a name="step-1-install-and-configure-windows-performance-analyzer"></a>步驟1：安裝及設定 Windows Performance Analyzer

WPA 是 Windows 評定及部署套件 (ADK) 所提供的追蹤檢視器。 它是一個獨立的公用程式，並不屬於您可以使用 Visual Studio 安裝程式安裝的元件。

目前只有 Windows ADK Insider Preview 提供支援 c + + 組建見解的 WPA 版本。 若要存取此預覽，您必須註冊 [Windows 測試人員計畫](https://insider.windows.com)。 您不需要安裝 Windows 10 Insider Preview 作業系統來取得 Windows ADK preview。 您只需要向 Windows 測試人員計畫註冊您的 Microsoft 帳戶。

### <a name="to-download-and-install-wpa"></a>下載並安裝 WPA

注意：安裝 Windows Performance Analyzer 需要 Windows 8 或更新版本。

1. 流覽至 Windows ADK [下載頁面](/windows-hardware/get-started/adk-install)。

1. 下載並安裝最新版本的 Windows ADK。

1. 當系統提示您想要安裝的功能時，請選取 [ **Windows 效能工具**組]。 您可以視需要選取其他功能，但不需要安裝 WPA。

   ![Windows Performance Analyzer 安裝程式的功能選取畫面](media/wpa-installation.png)

### <a name="to-configure-wpa"></a><a name="configuration-steps"></a> 設定 WPA

在 WPA 中查看 c + + Build Insights 追蹤需要特殊的增益集。 請依照下列步驟進行安裝：

1. 下載下列其中一個元件來取得增益集。 您不需要同時取得這兩者。 選擇您認為最方便的一個。
    1. [Visual Studio 2019 16.6 版和更新版本](https://visualstudio.microsoft.com/downloads/)，或
    1. [C + + Build Insights NuGet 套件](https://www.nuget.org/packages/Microsoft.Cpp.BuildInsights/)。

1. 將檔案複製 `perf_msvcbuildinsights.dll` 到您的 WPA 安裝目錄。
    1. 在 Visual Studio 2019 16.6 版和更新版本中，這個檔案位於： `C:\Program Files (x86)\Microsoft Visual Studio\2019\{Edition}\VC\Tools\MSVC\{Version}\bin\Host{Architecture}\{Architecture}` 。
    1. 在 c + + Build Insights NuGet 套件中，這個檔案位於： `wpa\{Architecture}` 。
    1. 在上述路徑中，將以大括弧括住的變數取代如下：
        1. `{Edition}` 是您的 Visual Studio 2019 版，例如「社團」、「專業版」或「企業」。
        1. `{Version}` 是您的 MSVC 版本。 選擇最高可用的版本。
        1. `{Architecture}`：選擇 `x64` 您是否有64位版本的 Windows。 否則，請選擇 `x86` 。
    1. WPA 安裝目錄通常是： `C:\Program Files (x86)\Windows Kits\10\Windows Performance Toolkit` 。

1. 在您的 WPA 安裝目錄中開啟檔案， `perfcore.ini` 並新增的專案 `perf_msvcbuildinsights.dll` 。

## <a name="step-2-trace-your-build-with-vcperfexe"></a>步驟2：使用 vcperf.exe 追蹤您的組建

若要查看 c + + Build Insights 資料，請先依照下列步驟將它收集至追蹤檔案：

1. 以系統管理員模式開啟**適用于 VS 2019**的**x64**或 x86 Native Tools 命令提示字元。  (以滑鼠右鍵按一下 [開始] 功能表專案，然後**選擇 [以**  >  **系統管理員身分執行**]。 ) 
    1. 如果您有64位版本的 Windows，請選擇 [ **x64** ]。 否則，請選擇 [ **x86**]。

1. 在命令提示字元視窗中，輸入下列命令：

   **vcperf.exe/start _SessionName_**

   選擇您要記住*的會話名稱。*

1. 像平常一樣建立您的專案。 您不需要使用相同的命令提示字元視窗來建立。

1. 在命令提示字元視窗中，輸入下列命令：

   **vcperf.exe/stop _SessionName_ _traceFile. etl_**

   請使用您之前為 *SessionName* 選擇的相同會話名稱。 選擇適當的 TraceFile 名稱作為 *etl* 追蹤檔。

以下是典型的 *vcperf.exe* 命令順序在開發人員命令提示字元視窗中的樣子：

![簡單的 vcperf.exe 使用案例](media/vcperf-simple-usage.png)

### <a name="important-notes-about-vcperfexe"></a>關於 vcperf.exe 的重要注意事項

- 需要有系統管理員許可權，才能啟動或停止 *vcperf.exe* 追蹤。 使用您使用 [以 **系統管理員身分執行**] 開啟的開發人員命令提示字元視窗。

- 一次只能有一個追蹤會話在電腦上執行。

- 請務必記住您用來啟動追蹤的會話名稱。 停止執行中的會話並不知道其名稱可能會很麻煩。

- 就像 *cl.exe* 和 *link.exe*一樣，命令列公用程式 *vcperf.exe* 包含在 MSVC 安裝中。 取得此元件不需要額外的步驟。

- *vcperf.exe* 會收集您系統上執行之所有 MSVC 工具的相關資訊。 因此，您不需要從用來收集追蹤的相同命令提示字元開始組建。 您可以從不同的命令提示字元，甚至是在 Visual Studio 中建立專案。

### <a name="vcperfexe-is-open-source"></a>vcperf.exe 是開放原始碼

如果您想要建立並執行您自己的 *vcperf.exe*版本，您可以從 [vcperf GitHub 存放庫](https://github.com/microsoft/vcperf)中複製它。

## <a name="step-3-view-your-trace-in-windows-performance-analyzer"></a>步驟3：在 Windows Performance Analyzer 中查看您的追蹤

啟動 WPA 並開啟您剛剛收集的追蹤。 WPA 應該將它辨識為 c + + Build Insights 追蹤，而且下列視圖應該會出現在左邊的 Graph Explorer 面板中：

- Build 總管
- 檔案儲存體
- 函數
- 範本具現化

如果您看不到這些視圖，請仔細檢查是否已正確設定 WPA，如 [步驟 1](#configuration-steps)所述。 您可以藉由將視圖拖曳至右邊的空白分析視窗來查看您的組建資料，如下所示：

![在 Windows Performance Analyzer 中查看 c + + Build Insights 追蹤](media/wpa-viewing-trace.gif)

您可以在 [Graph Explorer] 面板中找到其他的視圖。 當您對所包含的資訊感興趣時，請將它們拖曳到 [分析] 視窗中。 其中一個實用的 CPU (取樣) 視圖，以顯示整個組建的 CPU 使用率。

## <a name="more-information"></a>詳細資訊

[教學課程： Windows Performance Analyzer 基本概念](wpa-basics.md)\
深入瞭解可協助您分析組建追蹤的一般 WPA 作業。

[參考： vcperf 命令](../reference/vcperf-commands.md)\
*vcperf.exe*命令參考會列出所有可用的命令選項。

[參考： Windows Performance Analyzer 視圖](../reference/wpa-views.md)\
請參閱這篇文章，以取得有關 WPA 中 c + + 組建見解視圖的詳細資料。

[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)\
官方的 WPA 檔網站。

::: moniker-end
