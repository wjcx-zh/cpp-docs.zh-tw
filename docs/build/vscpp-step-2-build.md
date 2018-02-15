---
title: "建置並執行的 c + + 主控台應用程式專案 |Microsoft 文件"
description: "安裝 Visual c + + 的 Visual Studio 支援"
ms.custom: mvc
ms.date: 12/12/2017
ms.topic: get-started-article
ms.technology:
- devlang-C++
ms.devlang: C++
dev_langs:
- C++
ms.assetid: 45138d71-719d-42dc-90d7-1d0ca31a2f55
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2bbc2db5a86d44d2beabe32e265e91ddb0c90787
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="build-and-run-a-c-console-app-project"></a>建置並執行的 c + + 主控台應用程式專案

當您建立的 c + + 主控台應用程式專案，並輸入您的程式碼時，您可以建置並執行 Visual Studio 內以及然後加以執行為獨立應用程式從命令列。

## <a name="prerequisites"></a>必要條件

- 具有 c + + 工作負載，您的電腦上安裝並執行與桌面開發的 Visual Studio。 如果它尚未安裝，請依照下列中的步驟[安裝 c + + 支援 Visual Studio 中的](../build/vscpp-step-0-installation.md)。

- 建立"Hello，World ！" 專案，並輸入其原始程式碼。 如果您還沒有這麼做到尚未，請依照下列中的步驟[建立 c + + 主控台應用程式專案](../build/vscpp-step-1-create.md)。

如果 Visual Studio，看起來像這樣，您可以開始建置並執行您的應用程式：

   ![準備好要建置新專案](../build/media/vscpp-ready-to-build.png "準備好要建置新專案")

## <a name="build-and-run-your-code-in-visual-studio"></a>建置並執行 Visual Studio 中的程式碼

1. 若要建置專案，選擇 **建置方案**從**建置**功能表。 **輸出** 視窗會顯示在建置程序的結果。

   ![建置專案](../build/media/vscpp-build-solution.gif "建置專案")

1. 若要執行程式碼，在功能表列上，選擇 **偵錯**，**啟動但不偵錯**。

   ![啟動專案](../build/media/vscpp-start-without-debugging.gif "啟動專案")

    主控台視窗隨即開啟，並執行您的應用程式。 當您在 Visual Studio 啟動主控台應用程式時，它會執行您的程式碼，然後列印 「 按任意鍵繼續。 。 ." 若要讓您有機會，請參閱輸出。

恭喜您！ 您已建立您的第一個"Hello，world ！" 在 Visual Studio 中的主控台應用程式 ！ 按索引鍵，關閉主控台視窗並返回 Visual Studio。

[我遇到問題。](#build-and-run-your-code-in-visual-studio-issues)

## <a name="run-your-code-in-a-command-window"></a>在命令視窗中執行您的程式碼

通常您會在命令提示字元中，不會在 Visual Studio 中執行主控台應用程式。 由 Visual Studio 建置您的應用程式之後，您可以從任何命令視窗中執行它。 以下是如何尋找並執行新的應用程式中的命令提示字元視窗。

1. 在**方案總管 中**選取 HelloWorld 方案，以滑鼠右鍵按一下要開啟操作功能表。 選擇**在檔案總管 中開啟資料夾**開啟**檔案總管**HelloWorld 方案資料夾中的視窗。

1. 在**檔案總管**視窗中，開啟 [偵錯] 資料夾。 包含您的應用程式、 HelloWorld.exe，以及幾個其他偵錯的檔案。 選取 HelloWorld.exe、 按住 Shift 鍵並按一下滑鼠右鍵開啟內容功能表。 選擇**複製為路徑**複製到剪貼簿的應用程式的路徑。

1. 若要開啟 命令提示字元視窗，請按 Windows-R，以開啟**執行**對話方塊。 輸入*cmd.exe*中**開啟**文字方塊中，然後選擇 **確定**來執行命令提示字元視窗。

1. 在命令提示字元視窗中，以滑鼠右鍵按一下命令提示字元中，貼上您的應用程式的路徑。 按下 Enter，執行您的應用程式。

   ![在命令提示字元中執行應用程式](../build/media/vscpp-run-in-cmd.gif "在命令提示字元中執行應用程式")

恭喜，您所建置，並在 Visual Studio 中執行主控台應用程式 ！

[我遇到問題。](#run-your-code-in-a-command-window-issues)

## <a name="next-steps"></a>後續步驟

建置並執行這個簡單的應用程式之後，您已準備好進行更複雜的專案。 請參閱[使用 c + + 桌面開發的 Visual Studio IDE](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)如需詳細的逐步解說，瀏覽 Visual Studio 中的 Visual c + + 的功能。

## <a name="troubleshooting-guide"></a>疑難排解指南

過來的解決方案常見問題的解決當您建立第一個 c + + 專案。

### <a name="build-and-run-your-code-in-visual-studio-issues"></a>建置並執行您的程式碼在 Visual Studio 問題

紅色波浪線會顯示在原始碼程式碼編輯器中的任何項目之下，如果組建可能錯誤或警告。 檢查您的程式碼相符的拼字、 標點符號和案例的範例。

[返回。](#build-and-run-your-code-in-visual-studio)

### <a name="run-your-code-in-a-command-window-issues"></a>在命令視窗中執行程式碼問題

您也可以瀏覽至方案的偵錯資料夾，在命令列執行您的應用程式。 您無法從其他目錄中執行應用程式，而不指定應用程式路徑。 不過，您可以將您的應用程式複製到另一個目錄，並從該處執行。

如果您沒有看到**複製為路徑**快顯功能表中，關閉功能表，並接著按住 Shift 鍵，同時再次開啟。 這是為了方便起見。 您可以從 檔案總管 中搜尋 列複製到資料夾的路徑，並將它貼入**執行** 對話方塊中，然後輸入 最後可執行檔的名稱。 它會變得更強的但具有相同的結果。

[返回。](#run-your-code-in-a-command-window)


<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
