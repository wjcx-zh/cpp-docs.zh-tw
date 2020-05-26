---
title: 教學課程： vcperf 和 Windows Performance Analyzer
description: 如何使用 vcperf 和 WPA 來分析 c + + 組建追蹤的教學課程。
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 724df913400abb6d33c333f0a16c20fb982769bc
ms.sourcegitcommit: 98139766b548c55181ff5ec5ad3bfd9db2bf5c89
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/26/2020
ms.locfileid: "83865048"
---
# <a name="tutorial-vcperf-and-windows-performance-analyzer"></a>教學課程： vcperf 和 Windows Performance Analyzer

::: moniker range="<=vs-2017"

C + + Build Insights 工具可在 Visual Studio 2019 中取得。 若要查看此版本的檔，請將本文的 Visual Studio**版本**選取器控制項設定為 Visual Studio 2019。 您可在此頁面的目錄頂端找到該檔案。

::: moniker-end
::: moniker range="vs-2019"

在本教學課程中，您將瞭解如何使用*vcperf*來收集 c + + 組建的追蹤。 您也將瞭解如何在 Windows Performance Analyzer 中查看此追蹤。

## <a name="step-1-install-and-configure-windows-performance-analyzer"></a>步驟1：安裝及設定 Windows Performance Analyzer

WPA 是 Windows 評定及部署套件（ADK）中提供的追蹤檢視器。 這是獨立的公用程式，不屬於您可以使用 Visual Studio 安裝程式安裝的元件。

支援 c + + Build Insights 的 WPA 版本目前僅適用于 Windows ADK Insider preview。 若要存取此預覽，您必須註冊[Windows 測試人員計畫](https://insider.windows.com)。 您不需要安裝 Windows 10 Insider preview 作業系統來取得 Windows ADK preview。 您只需要向 Windows 測試人員程式註冊您的 Microsoft 帳戶。

### <a name="to-download-and-install-wpa"></a>下載並安裝 WPA

注意：安裝 Windows Performance Analyzer 需要 Windows 8 或更新版本。

1. 流覽至 Windows ADK[下載頁面](https://docs.microsoft.com/windows-hardware/get-started/adk-install)。

1. 下載並安裝最新版的 Windows ADK。

1. 當系統提示您想要安裝的功能時，請選取 [ **Windows 效能工具**組]。 您可以視需要選取其他功能，但不需要安裝 WPA。

   ![Windows Performance Analyzer 安裝程式的功能選取畫面](media/wpa-installation.png)

### <a name="to-configure-wpa"></a><a name="configuration-steps"></a>設定 WPA

在 WPA 中觀看 c + + Build Insights 追蹤需要特殊的增益集。 請依照下列步驟進行安裝：

1. 下載下列其中一個元件來取得增益集。 您不需要同時取得這兩者。 選擇您認為最方便的一個。
    1. [Visual Studio 2019 16.6 版和更新版本](https://visualstudio.microsoft.com/downloads/)，或
    1. [C + + Build Insights NuGet 套件](https://www.nuget.org/packages/Microsoft.Cpp.BuildInsights/)。

1. 將檔案複製 `perf_msvcbuildinsights.dll` 到您的 WPA 安裝目錄。
    1. 在 Visual Studio 2019 16.6 版和更新版本中，此檔案位於： `C:\Program Files (x86)\Microsoft Visual Studio\2019\{Edition}\VC\Tools\MSVC\{Version}\bin\Host{Architecture}\{Architecture}` 。
    1. 在 c + + Build Insights NuGet 套件中，此檔案位於： `wpa\{Architecture}` 。
    1. 在上述路徑中，將以大括弧括住的變數取代為，如下所示：
        1. `{Edition}`是您的 Visual Studio 2019 版本，例如「社區」、「專業」或「企業」。
        1. `{Version}`是您的 MSVC 版本。 選擇最高可用的一個。
        1. `{Architecture}`： `x64` 如果您有64位版本的 Windows，請選擇。 否則，請選擇 `x86` 。
    1. WPA 安裝目錄通常是： `C:\Program Files (x86)\Windows Kits\10\Windows Performance Toolkit` 。

1. 在您的 WPA 安裝目錄中，開啟檔案 `perfcore.ini` 並新增的專案 `perf_msvcbuildinsights.dll` 。

## <a name="step-2-trace-your-build-with-vcperfexe"></a>步驟2：使用 vcperf 追蹤組建

若要查看 c + + Build Insights 資料，請先遵循下列步驟，將它收集到追蹤檔案中：

1. 在系統管理員模式中開啟**適用于 VS 2019**的**x64**或 x86 Native Tools 命令提示字元。 （以滑鼠右鍵按一下 [開始] 功能表項目，然後選擇 [**更多**  >  ]**以系統管理員身分執行**。）
    1. 如果您有64位版本的 Windows，請選擇 [ **x64** ]。 否則，請選擇 [ **x86**]。

1. 在 [命令提示字元] 視窗中，輸入下列命令：

   **vcperf .exe/start _SessionName_**

   選擇 [會話名稱]，您會記住 [ *SessionName*]。

1. 像平常一樣建立您的專案。 您不需要使用相同的命令提示字元視窗來建立。

1. 在 [命令提示字元] 視窗中，輸入下列命令：

   **vcperf .exe/stop _SessionName_ _traceFile .etl_**

   使用您之前為*SessionName*選擇的會話名稱。 為 [ *traceFile* ] 追蹤檔案選擇適當的名稱。

以下是典型的*vcperf*命令順序在開發人員命令提示字元視窗中的樣子：

![簡單的 vcperf 使用案例](media/vcperf-simple-usage.png)

### <a name="important-notes-about-vcperfexe"></a>關於 vcperf 的重要注意事項

- 必須有系統管理員許可權，才能啟動或停止*vcperf*追蹤。 使用您使用 [以**系統管理員身分執行**] 開啟的開發人員命令提示字元視窗。

- 一次只能有一個追蹤會話在機器上執行。

- 請務必記住您用來啟動追蹤的會話名稱。 停止執行中的會話並不知道它的名稱，可能會有麻煩。

- 就像*cl* *和 node.js，命令*行公用程式*vcperf*會包含在 MSVC 安裝中。 取得此元件不需要額外的步驟。

- *vcperf*會收集在您系統上執行之所有 MSVC 工具的相關資訊。 因此，您不需要從用來收集追蹤的同一個命令提示字元啟動組建。 您可以從不同的命令提示字元，或甚至在 Visual Studio 中建立專案。

### <a name="vcperfexe-is-open-source"></a>vcperf 是開放原始碼

如果您想要建立並執行自己的*vcperf*版本，請隨意從[vcperf GitHub 存放庫](https://github.com/microsoft/vcperf)複製它。

## <a name="step-3-view-your-trace-in-windows-performance-analyzer"></a>步驟3：在 Windows 效能分析程式中查看您的追蹤

啟動 WPA，並開啟您剛收集的追蹤。 WPA 應該將它辨識為 c + + Build Insights 追蹤，而下列視圖應該會出現在左邊的 Graph Explorer 面板中：

- Build 總管
- 檔案儲存體
- 函數
- 範本具現化

如果您看不到這些視圖，請仔細檢查 WPA 已正確設定，如[步驟 1](#configuration-steps)所述。 您可以將視圖拖曳至右邊的空白分析視窗，以查看組建資料，如下所示：

![在 Windows Performance Analyzer 中查看 c + + Build Insights 追蹤](media/wpa-viewing-trace.gif)

其他視圖則可在 [Graph Explorer] 面板中使用。 當您對所包含的資訊感興趣時，請將它們拖曳到 [分析] 視窗中。 [CPU （取樣）] 視圖是很有用的，其中顯示整個組建的 CPU 使用率。

## <a name="more-information"></a>詳細資訊

[教學課程： Windows Performance Analyzer 基本概念](wpa-basics.md)\
深入瞭解可協助您分析組建追蹤的常見 WPA 作業。

[參考： vcperf 命令](/cpp/build-insights/reference/vcperf-commands)\
*Vcperf*命令參考會列出所有可用的命令選項。

[參考： Windows Performance Analyzer views](/cpp/build-insights/reference/wpa-views)\
請參閱這篇文章，以取得 WPA 中 c + + Build Insights views 的詳細資訊。

[Windows 效能分析程式](/windows-hardware/test/wpt/windows-performance-analyzer)\
官方的 WPA 檔網站。

::: moniker-end
