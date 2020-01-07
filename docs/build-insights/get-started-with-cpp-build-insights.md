---
title: 開始使用 C++ 組建見解
description: 如何使用 build Insights 中的組建階段效能分析工具C++的高階總覽。
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 862bfae3bdb27812306dcd356aecab812ea5181c
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75298736"
---
# <a name="get-started-with-c-build-insights"></a>開始使用 C++ 組建見解

::: moniker range="<=vs-2017"

Visual Studio C++ 2019 中提供 Build Insights 工具。 若要查看該版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2019。

::: moniker-end
::: moniker range="vs-2019"

C++Build Insights 是一組工具，可讓您更深入瞭解 Microsoft Visual C++ （MSVC）工具鏈。 工具會收集有關您C++組建的資料，並以可協助您回答常見問題的格式呈現，例如：

- 我的組建是否充分平行化？
- 我應該在預先編譯的標頭（PCH）中包含哪些內容？
- 是否有特定的瓶頸需要專注于增加組建速度？

這項技術的兩個主要元件是命令列公用程式*vcperf* ，以及適用于 Windows Performance ANALYZER （WPA）追蹤檢視器的增益集。 公用程式是用來收集組建的追蹤，而增益集可讓您在 WPA 中進行查看。 請遵循下列步驟，開始使用這兩個工具。

## <a name="step-1-install-and-configure-windows-performance-analyzer"></a>步驟1：安裝及設定 Windows Performance Analyzer

WPA 是 Windows 評定及部署套件（ADK）中提供的追蹤檢視器。 這是獨立的公用程式，不屬於您可以使用 Visual Studio 安裝程式安裝的元件。

支援C++ Build INSIGHTS 的 WPA 版本目前僅適用于 Windows ADK Insider preview。 若要存取此預覽，您必須註冊[Windows 測試人員計畫](https://insider.windows.com)。 您不需要安裝 Windows 10 Insider preview 作業系統來取得 Windows ADK preview。 您只需要向 Windows 測試人員程式註冊您的 Microsoft 帳戶。

### <a name="to-download-and-install-wpa"></a>下載並安裝 WPA

注意：安裝 Windows Performance Analyzer 需要 Windows 8 或更新版本。

1. 流覽至 Windows ADK Insider Preview[下載頁面](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewADK)。

1. 下載 Windows ADK Insider preview。 這是磁片映射。

1. 開啟磁片映射，然後執行*adksetup.exe*安裝程式。

1. 當系統提示您想要安裝的功能時，請選取 [ **Windows 效能工具**組]。 您可以視需要選取其他功能，但不需要安裝 WPA。

   ![Windows Performance Analyzer 安裝程式的功能選取畫面](media/wpa-installation.png)

### <a name="configuration-steps"></a>設定組建深入解析

1. 啟動 WPA。

1. 選取 [**視窗]** >**選取 [資料表（實驗性）** ]。

1. 向下流覽至 [**診斷**] 區段。

1. 選取所有 MSVC Build Insights views。

   ![Windows Performance Analyzer 的資料表選取面板](media/wpa-configuration.png)

## <a name="step-2-trace-your-build-with-vcperfexe"></a>步驟2：使用 vcperf 追蹤組建

若要C++查看 Build Insights 資料，請先遵循下列步驟，將它收集到追蹤檔案：

1. 在系統管理員模式中，開啟 Visual Studio 2019 的原生工具或跨工具開發人員命令提示字元。 （以滑鼠右鍵按一下 [開始] 功能表項目，然後選擇 [**更多** > 以**系統管理員身分執行**]）。

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

## <a name="step-3-view-your-trace-in-windows-performance-analyzer"></a>步驟3：在 Windows 效能分析程式中查看您的追蹤

啟動 WPA，並開啟您剛收集的追蹤。 WPA 應該將它辨識為C++ 「組建深入解析」追蹤，而下列視圖應該會出現在左邊的 Graph Explorer 面板中：

- Build 總管
- 檔案
- 函數

如果您看不到這些視圖，請仔細檢查 WPA 已正確設定，如[步驟 1](#configuration-steps)所述。 您可以將視圖拖曳至右邊的空白分析視窗，以查看組建資料，如下所示：

![在 Windows C++ Performance Analyzer 中查看 Build Insights 追蹤](media/wpa-viewing-trace.gif)

其他視圖則可在 [Graph Explorer] 面板中使用。 當您對所包含的資訊感興趣時，請將它們拖曳到 [分析] 視窗中。 [CPU （取樣）] 視圖是很有用的，其中顯示整個組建的 CPU 使用率。

## <a name="more-information"></a>詳細資訊

[Windows Performance Analyzer 基本概念](wpa-basics.md)\
深入瞭解可協助您分析組建追蹤的常見 WPA 作業。

[vcperf .exe 參考](vcperf-reference.md)\
*Vcperf*命令參考會列出所有可用的命令選項。

[Windows Performance Analyzer views 參考](wpa-views-reference.md)\
請參閱這篇文章，以取得C++有關 WPA 中的組建深入解析視圖的詳細資訊。

[Windows 效能分析](/windows-hardware/test/wpt/windows-performance-analyzer)程式\
官方的 WPA 檔網站。

::: moniker-end
