---
title: 建置並執行 c + + 主控台應用程式專案
description: 建置並執行 Hello World 主控台應用程式中 Visual c + +
ms.custom: mvc
ms.date: 12/12/2017
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d71-719d-42dc-90d7-1d0ca31a2f55
ms.openlocfilehash: 09780d5823190eb4cb3b4ad13bb60e33808e4987
ms.sourcegitcommit: beeb77b2976e997debc55b1af35024cc62e62799
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/06/2018
ms.locfileid: "52977728"
---
# <a name="build-and-run-a-c-console-app-project"></a>建置並執行 c + + 主控台應用程式專案

當您已建立的 c + + 主控台應用程式專案，並輸入您的程式碼時，您可以建置和執行在 Visual Studio 中，然後依照做為獨立的應用程式從命令列執行它。

## <a name="prerequisites"></a>必要條件

- 具有 c + + 工作負載中，使用您的電腦上安裝和執行 Visual Studio 中使用的桌面開發。 如果它尚未安裝，請依照下列中的步驟[Visual Studio 中的安裝 c + + 支援](../build/vscpp-step-0-installation.md)。

- 建立"Hello，World ！" 專案，然後輸入其原始程式碼。 如果您還沒有這麼做，請依照下列中的步驟[建立 c + + 主控台應用程式專案](../build/vscpp-step-1-create.md)。

如果 Visual Studio 看起來像這樣，您就可以建置並執行您的應用程式項目：

   ![準備好要建置新的專案](../build/media/vscpp-ready-to-build.png "準備好要建置新的專案")

## <a name="build-and-run-your-code-in-visual-studio"></a>建置並執行 Visual Studio 中的程式碼

1. 若要建置專案時，選擇**建置方案**從**建置**功能表。 **輸出**視窗會顯示在建置程序的結果。

   ![建置專案](../build/media/vscpp-build-solution.gif "建置專案")

1. 若要執行的程式碼，在功能表列上，選擇**偵錯**，**啟動但不偵錯**。

   ![啟動專案](../build/media/vscpp-start-without-debugging.gif "啟動專案")

   主控台視窗隨即開啟，然後再執行您的應用程式。 當您在 Visual Studio 啟動主控台應用程式時，它會執行您的程式碼，則會列印 「 按任意鍵繼續。 。 ." 若要讓您以查看輸出的機率。

恭喜您！ 您已建立您的第一個"Hello，world ！" 在 Visual Studio 中的主控台應用程式 ！ 按任一鍵關閉主控台視窗並返回 Visual Studio。

[我遇到問題。](#build-and-run-your-code-in-visual-studio-issues)

## <a name="run-your-code-in-a-command-window"></a>在命令視窗中執行您的程式碼

一般來說，您會在命令提示字元中，不會在 Visual Studio 中執行主控台應用程式。 一旦 Visual studio 建置您的應用程式時，您可以從任何命令視窗中執行它。 以下是如何尋找和執行新的應用程式中的命令提示字元視窗。

1. 在 [**方案總管] 中**選取 HelloWorld 方案，以滑鼠右鍵按一下以開啟操作功能表。 選擇**在檔案總管 中開啟資料夾**來開啟**檔案總管**HelloWorld 方案資料夾中的視窗。

1. 在 [**檔案總管**] 視窗中，開啟 [偵錯] 資料夾。 這包含您的應用程式中，HelloWorld.exe 和幾個其他偵錯的檔案。 選取 HelloWorld.exe、 按住 Shift 鍵並按一下滑鼠右鍵開啟操作功能表。 選擇**複製為路徑**複製到剪貼簿的應用程式的路徑。

1. 若要開啟命令提示字元 視窗，請按 Windows R，以開啟**執行**對話方塊。 輸入*cmd.exe*中**開放**文字方塊中，然後選擇**確定**來執行命令提示字元視窗。

1. 在 命令提示字元 視窗中，以滑鼠右鍵按一下要將您的應用程式的路徑貼到 命令提示字元。 按下 Enter，執行您的應用程式。

   ![在命令提示字元中執行應用程式](../build/media/vscpp-run-in-cmd.gif "在命令提示字元中執行應用程式")

恭喜，您已經建立，並在 Visual Studio 中執行主控台應用程式 ！

[我遇到問題。](#run-your-code-in-a-command-window-issues)

## <a name="next-steps"></a>後續步驟

一旦您已經建立並執行這個簡單的應用程式，您準備好進行更複雜的專案項目。 請參閱[使用 Visual Studio IDE 進行 c + + 桌面程式開發](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)如需詳細的逐步解說，探索 Visual Studio 中的 Visual c + + 的功能。

## <a name="troubleshooting-guide"></a>疑難排解指南

來這裡解決方案常見問題的解決當您建立第一個 c + + 專案。

### <a name="build-and-run-your-code-in-visual-studio-issues"></a>建置並執行您的程式碼在 Visual Studio 問題

如果紅色的波浪線會顯示在原始碼程式碼編輯器中的任何項目之下，組建可能會有錯誤或警告。 檢查您的程式碼符合拼字、 標點符號及案例的範例。

[返回。](#build-and-run-your-code-in-visual-studio)

### <a name="run-your-code-in-a-command-window-issues"></a>在命令視窗中執行程式碼問題

您也可以瀏覽至方案的偵錯資料夾，在命令列來執行您的應用程式。 您無法從其他目錄中執行您的應用程式，但未指定應用程式的路徑。 不過，您可以將您的應用程式複製到另一個目錄，並從該處執行。

如果您沒有看到**複製為路徑**在快顯功能表中，關閉功能表，，和時再次開啟，然後按住 Shift 鍵。 這只是為了方便起見。 您也可以將路徑複製到資料夾中，從 檔案總管 中搜尋 列中，並將它貼至**執行** 對話方塊中，然後輸入 最後可執行檔的名稱。 它會變得更強的但它有相同的結果。

[返回。](#run-your-code-in-a-command-window)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
