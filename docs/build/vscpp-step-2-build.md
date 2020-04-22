---
title: 建置並執行 C++ 主控台應用程式專案
description: 在可視化C++中構建並運行 Hello World 控制台應用
ms.custom: mvc
ms.date: 04/20/2020
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d71-719d-42dc-90d7-1d0ca31a2f55
ms.openlocfilehash: d1e92e598b370312730a7c4e208b935a264010bf
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749250"
---
# <a name="build-and-run-a-c-console-app-project"></a>建置並執行 C++ 主控台應用程式專案

您已經創建了一個C++控制台應用專案並輸入了代碼。 現在,您可以在可視化工作室中構建和運行它。 然後,從命令行作為獨立應用運行它。

## <a name="prerequisites"></a>Prerequisites

- 安裝 Visual Studio 和使用 C++ 進行桌面開發工作負載，並在您的電腦上執行。 如果尚未安裝,請按照[「安裝C++視覺工作室中支援](vscpp-step-0-installation.md)的步驟操作。

- 創建一個"你好,世界! 專案並輸入其原始程式碼。 如果尚未完成此步驟,請按照[C++控制台應用專案](vscpp-step-1-create.md)中的步驟操作。

如果 Visual Studio 如下所示,則可以構建和運行應用:

   ![準備建置新項目](media/vscpp-ready-to-build.png "準備建置新項目")

## <a name="build-and-run-your-code-in-visual-studio"></a>在視覺化工作室中建構與執行代碼

1. 若要建置您的專案，請從 [建置]**** 功能表中選擇 [建置方案]****。 [輸出]**** 視窗會顯示建置過程的結果。

   ![組建項目](media/vscpp-build-solution.gif "建置專案")

1. 若要執行程式碼，請在功能表列上，選擇 [偵錯]****、[啟動但不偵錯]****。

   ![啟動專案](media/vscpp-start-without-debugging.gif "啟動專案")

   主控台視窗會隨即開啟並執行您的應用程式。 當您在 Visual Studio 中啟動主控台應用程式時，它會執行您的程式碼，然後印出「請按任意鍵繼續 . ." 讓您可以有機會查看輸出。

恭喜！ 您已在 Visual Studio 中建立了您的第一個 "Hello, world!" 主控台應用程式！ 請按任意鍵關閉主控台視窗並返回 Visual Studio。

[發生問題。](#build-and-run-your-code-in-visual-studio-issues)

## <a name="run-your-code-in-a-command-window"></a>在命令視窗中執行代碼

通常,在命令提示符下運行主控台應用,而不是在Visual Studio中運行主控台應用。 應用由 Visual Studio 構建後,可以從任何命令視窗運行它。 下面瞭解如何在命令提示視窗中尋找和運行新應用。

1. 在**解決方案資源管理器中**,選擇 HelloWorld 解決方案(不是 HelloWorld 專案),然後右鍵單擊以打開上下文菜單。 選擇 **「檔案資源管理器中的打開資料夾**」以在 HelloWorld 解決方案資料夾中打開**檔案資源管理器**視窗。

1. 在 **「檔案資源管理員」** 視窗中,打開除錯資料夾。 此資料夾包含您的應用程式*HelloWorld.exe,* 以及其他幾個調試檔。 按住**Shift**鍵並右鍵單擊*HelloWorld.exe*以打開上下文菜單。 選擇 **「複製為路徑」** 以將路徑複製到剪貼簿。

1. 要打開命令提示視窗,請按**Windows+R**打開 **「執行」** 對話框。 在 **「打開**文字」框中輸入*cmd.exe,* 然後選擇 **「確定」** 以執行命令提示視窗。

1. 在命令提示視窗中,右鍵單擊以將應用的路徑粘貼到命令提示符中。 按 Enter 以運行應用。

   ![在指令提示符下執行應用](media/vscpp-run-in-cmd.gif "在指令提示符下執行應用")

恭喜您,您在 Visual Studio 中構建並運行了一個主控台應用程式!

[發生問題。](#run-your-code-in-a-command-window-issues)

## <a name="next-steps"></a>後續步驟

構建並運行此簡單應用后,即可完成更複雜的專案。 有關詳細資訊,請參閱[使用視覺化工作室 IDE 進行C++桌面開發](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)。 它有更詳細的演練,探索微軟C++在視覺工作室的功能。

## <a name="troubleshooting-guide"></a>疑難排解指南

創建第一個C++專案時,請在此處尋求常見問題的解決方案。

### <a name="build-and-run-your-code-in-visual-studio-issues"></a>在視覺化工作室中建構和執行代碼:問題

如果原始碼編輯器中的任何內容下出現紅色波浪,則生成可能有錯誤或警告。 檢查代碼是否與拼寫、標點符號和大小寫中的範例匹配。

[回去。](#build-and-run-your-code-in-visual-studio)

### <a name="run-your-code-in-a-command-window-issues"></a>在命令視窗中執行代碼:問題

如果檔案資源管理器中顯示的路徑在*\\HelloWorld\\HelloWorld*中結束,您已經打開了 HelloWorld*專案*,而不是 HelloWorld*解決方案*。 您將被不包含應用的 Debug 資料夾混淆。 在文件資源管理器中導航一個級別,以訪問解決方案資料夾,這是路徑中的第一個*HelloWorld。* 此資料夾還包含一個除錯資料夾,您將在那裡找到你的應用。

您還可以導航到命令列上的解決方案調試資料夾以運行應用。 如果不指定應用的路徑,你的應用不會從其他目錄運行。 但是,您可以將應用複製到其他目錄,並從那裡運行它。 還可以將其複製到 PATH 環境變數指定的目錄,然後從任何位置運行它。

如果在快捷菜單中未將 **「複製」視為路徑**,請關閉功能表,然後在再次打開 **「Shift」** 鍵時按住該鍵。 此命令只是為了方便起見。 還可以從檔案資源管理器搜索欄將路徑複製到資料夾,並將其貼上到 **「執行」** 對話框中,然後在末尾輸入可執行檔的名稱。 只是打字多一點,但結果相同。

[回去。](#run-your-code-in-a-command-window)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
