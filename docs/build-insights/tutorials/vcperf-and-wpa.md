---
title: 教學:vcperf 與 Windows 效能分析器
description: 關於如何使用 vcperf 和 WPA 分析C++生成跟蹤的教程。
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c22f3dfddfd346d4f0eee898cb5164fd8923336e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323416"
---
# <a name="tutorial-vcperf-and-windows-performance-analyzer"></a>教學:vcperf 與 Windows 效能分析器

::: moniker range="<=vs-2017"

C++構建見解工具可在 Visual Studio 2019 中使用。 要查看此版本的文檔,請將本文的可視化工作室**版本**選擇器控制項設定為 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range="vs-2019"

在本教程中,您將學習如何使用*vcperf.exe*收集C++生成的痕跡。 您還將瞭解如何在 Windows 性能分析器中查看此追蹤。

## <a name="step-1-install-and-configure-windows-performance-analyzer"></a>第一步:安裝與設定 Windows 效能分析器

WPA 是 Windows 評估和部署工具組 (ADK) 中可用的追蹤檢視器。 它是一個單獨的實用程式,不屬於您可以使用 Visual Studio 安裝程式安裝的元件。

支援C++生成見解的 WPA 版本目前僅在 Windows ADK 預覽版中提供。 要存取此預覽版,您必須註冊 Windows[預覽版程式](https://insider.windows.com)。 您無需安裝 Windows 10 預覽版作業系統來獲取 Windows ADK 預覽。 您只需向 Windows 預覽版計劃註冊您的 Microsoft 帳戶。

### <a name="to-download-and-install-wpa"></a>下載並安裝 WPA

注意:安裝 Windows 性能分析器需要 Windows 8 或以上。

1. 瀏覽到 Windows ADK 預覽預覽[下載頁面](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewADK)。

1. 下載 Windows ADK 預覽版。 它是磁片映射。

1. 開啟磁碟映射並運行*adksetup.exe*安裝程式。

1. 當提示要安裝的功能時,請選擇**Windows 效能工具套件**。 如果需要,您可以選擇其他功能,但它們不需要安裝 WPA。

   ![Windows 效能分析器安裝程式的功能選擇螢幕](media/wpa-installation.png)

### <a name="to-configure-build-insights"></a><a name="configuration-steps"></a>設定產生見解

1. 啟動 WPA。

1. 選擇**視窗**>**選擇表(實驗)。**

1. 向下滾動到**診斷**部分。

1. 選擇所有 MSVC 生成見解檢視。

   ![Windows 效能分析器的表選擇面板](media/wpa-configuration.png)

## <a name="step-2-trace-your-build-with-vcperfexe"></a>第二步:使用 vcperf.exe 追蹤您的產生

要檢視C++生成見解資料,首先通過以下步驟將其收集到跟蹤檔中:

1. 在管理員模式下打開 Visual Studio 2019 的本機工具或交叉工具開發人員命令提示。 (右鍵按兩下"開始"菜單項,然後選擇 **"以管理員** > **身份運行**更多"。

1. 在指令提示視窗中, 輸入以下指令:

   **vcperf.exe /啟動_工作階段名稱_**

   選擇工作*階段 名稱的作業階段名稱*。

1. 像您通常一樣構建專案。 不需要使用相同的命令提示視窗來生成。

1. 在指令提示視窗中, 輸入以下指令:

   **vcperf.exe /停止_工作階段名稱名稱__追蹤檔案.etl_**

   使用之前為*會話名稱*選擇的相同會話名稱。 為*追蹤檔.etl*追蹤檔案選擇適當的名稱。

以下是典型的*vcperf.exe*命令序列在開發人員命令提示視窗中的外觀:

![簡單的 vcperf.exe 使用機制](media/vcperf-simple-usage.png)

### <a name="important-notes-about-vcperfexe"></a>關於vcperf.exe的重要說明

- 啟動或停止*vcperf.exe*追蹤需要管理員許可權。 使用使用 **「作為管理員運行」** 打開的開發人員命令提示視窗。

- 一次只能運行一個跟蹤會話。

- 請確保記住用於啟動跟蹤的作業階段名稱。 在不知道正在運行的工作階段名稱的情況下停止正在運行的作業階段可能很麻煩。

- 就像*cl.exe*和*link.exe*一樣,命令行實用程式*vcperf.exe*包含在MSVC安裝中。 不需要執行其他步驟即可獲取此元件。

- *vcperf.exe*收集有關系統上運行的所有 MSVC 工具的資訊。 因此,您不必從用於收集跟蹤的同一命令提示啟動生成。 可以從不同的命令提示符,甚至 Visual Studio 中生成專案。

## <a name="step-3-view-your-trace-in-windows-performance-analyzer"></a>第三步:在 Windows 效能分析器中檢視追蹤

啟動 WPA 並打開您剛剛收集的追蹤。 WPA 應將其識別為C++生成見解跟蹤,並且以下視圖應出現在左側的圖形資源管理器面板中:

- Build 總管
- 檔案
- 函式

如果看不到這些檢視,請仔細檢查 WPA 配置是否正確,如[步驟 1](#configuration-steps)中所述。 通過將檢視拖動到右側的空分析視窗中,可以查看生成數據,如下所示:

![在 Windows 效能分析器中檢視C++產生見解追蹤](media/wpa-viewing-trace.gif)

其他檢視在「圖形資源管理器」面板中可用。 當您對它們包含的資訊感興趣時,將它們拖到"分析"視窗中。 有用的檢視是 CPU(取樣)視圖,它顯示了整個生成中的 CPU 利用率。

## <a name="more-information"></a>詳細資訊

[教學:Windows 效能分析器基礎知識](wpa-basics.md)\
瞭解可説明您分析生成跟蹤的常見 WPA 操作。

[參考: vcperf 指令](/cpp/build-insights/reference/vcperf-commands)\
*vcperf.exe*命令引用列出了所有可用的命令選項。

[參考:Windows 效能分析器檢視](/cpp/build-insights/reference/wpa-views)\
有關 WPA 中C++生成見解視圖的詳細資訊,請參閱本文。

[Windows 效能分析器](/windows-hardware/test/wpt/windows-performance-analyzer)\
正式 WPA 文件網站。

::: moniker-end
