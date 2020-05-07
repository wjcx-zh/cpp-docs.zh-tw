---
title: 建置並執行 C++ 主控台應用程式專案
description: 在 Visual C++ 中建立並執行 Hello World 主控台應用程式
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

您已建立 c + + 主控台應用程式專案並輸入程式碼。 現在您可以在 Visual Studio 內建立並執行它。 然後，從命令列，以獨立應用程式的形式執行它。

## <a name="prerequisites"></a>必要條件

- 安裝 Visual Studio 和使用 C++ 進行桌面開發工作負載，並在您的電腦上執行。 如果尚未安裝，請遵循在[Visual Studio 中安裝 c + + 支援](vscpp-step-0-installation.md)中的步驟。

- 建立 "Hello，World！" 專案，並輸入其原始程式碼。 如果您尚未完成這個步驟，請依照[建立 c + + 主控台應用程式專案](vscpp-step-1-create.md)中的步驟進行。

如果 Visual Studio 看起來像這樣，您就可以開始建立並執行您的應用程式：

   ![準備好建立新專案](media/vscpp-ready-to-build.png "準備好建立新專案")

## <a name="build-and-run-your-code-in-visual-studio"></a>在 Visual Studio 中建立並執行您的程式碼

1. 若要建置您的專案，請從 [建置]**** 功能表中選擇 [建置方案]****。 [輸出]**** 視窗會顯示建置過程的結果。

   ![建立專案](media/vscpp-build-solution.gif "建置專案")

1. 若要執行程式碼，請在功能表列上，選擇 [偵錯]****、[啟動但不偵錯]****。

   ![啟動專案](media/vscpp-start-without-debugging.gif "啟動專案")

   主控台視窗會隨即開啟並執行您的應用程式。 當您在 Visual Studio 中啟動主控台應用程式時，它會執行您的程式碼，然後印出「請按任意鍵繼續 . ." 讓您可以有機會查看輸出。

恭喜！ 您已在 Visual Studio 中建立了您的第一個 "Hello, world!" 主控台應用程式！ 請按任意鍵關閉主控台視窗並返回 Visual Studio。

[發生問題。](#build-and-run-your-code-in-visual-studio-issues)

## <a name="run-your-code-in-a-command-window"></a>在命令視窗中執行您的程式碼

一般來說，您會在命令提示字元中執行主控台應用程式，而不是在 Visual Studio 中。 一旦 Visual Studio 建立您的應用程式，您就可以從任何命令視窗執行。 以下說明如何在 [命令提示字元] 視窗中尋找並執行新的應用程式。

1. 在**方案總管**中，選取 [HelloWorld] 方案（而非 HelloWorld 專案），然後按一下滑鼠右鍵以開啟內容功能表。 選擇 [檔案**瀏覽器] 中的 [開啟資料夾**]，在 HelloWorld 方案資料夾中開啟 [檔案**瀏覽器**] 視窗。

1. 在 [檔案**瀏覽器**] 視窗中，開啟 [Debug] 資料夾。 此資料夾包含您的應用程式、 *HelloWorld*和幾個其他的偵錯工具檔案。 按住**Shift**鍵並以滑鼠右鍵按一下 [ *HelloWorld* ]，以開啟內容功能表。 選擇 [**複製為路徑**]，將應用程式的路徑複製到剪貼簿。

1. 若要開啟 [命令提示字元] 視窗，請按**Windows + R**以開啟 [**執行**] 對話方塊。 在 [**開啟**] 文字方塊中輸入*cmd.exe* ，然後選擇 **[確定**] 以執行 [命令提示字元] 視窗。

1. 在 [命令提示字元] 視窗中，以滑鼠右鍵按一下以在命令提示字元中貼上您應用程式的路徑。 按 Enter 鍵以執行您的應用程式。

   ![在命令提示字元中執行應用程式](media/vscpp-run-in-cmd.gif "在命令提示字元中執行應用程式")

恭喜，您已在 Visual Studio 中建立並執行主控台應用程式！

[發生問題。](#run-your-code-in-a-command-window-issues)

## <a name="next-steps"></a>後續步驟

建立並執行此簡單應用程式之後，您就可以開始進行更複雜的專案。 如需詳細資訊，請參閱[使用 VISUAL STUDIO IDE 進行 c + + 桌面程式開發](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)。 其中有更詳細的逐步解說，說明如何在 Visual Studio 中探索 Microsoft c + + 的功能。

## <a name="troubleshooting-guide"></a>疑難排解指南

當您建立第一個 c + + 專案時，請前往這裡取得常見問題的解決方案。

### <a name="build-and-run-your-code-in-visual-studio-issues"></a>在 Visual Studio 中建立並執行您的程式碼：問題

如果 [原始程式碼編輯器] 中的 [任何專案] 底下出現紅色波浪線，表示組建可能有錯誤或警告。 檢查您的程式碼是否符合拼寫、標點符號和大小寫中的範例。

[回去。](#build-and-run-your-code-in-visual-studio)

### <a name="run-your-code-in-a-command-window-issues"></a>在命令視窗中執行您的程式碼：問題

如果 [檔案管理器] 中顯示的路徑結尾為* \\HelloWorld\\HelloWorld*，則您已開啟 HelloWorld*專案*，而不是 HelloWorld*方案*。 您會因為不包含您應用程式的 Debug 資料夾而感到困惑。 在 [檔案瀏覽器] 中流覽層級，以移至方案資料夾，也就是路徑中的第一個*HelloWorld* 。 此資料夾也包含 [Debug] 資料夾，您可以在該處找到您的應用程式。

您也可以在命令列流覽至 [解決方案 Debug] 資料夾，以執行您的應用程式。 您的應用程式不會從其他目錄執行，而不需指定應用程式的路徑。 不過，您可以將應用程式複製到另一個目錄，並從該處執行。 您也可以將它複製到 PATH 環境變數所指定的目錄，然後從任何地方執行它。

如果您在快捷方式功能表中看不到 [**複製為路徑**]，請關閉功能表，然後按住**Shift**鍵，再重新開啟它。 此命令只是為了方便起見。 您也可以從 [檔案瀏覽器] 搜尋列複製資料夾的路徑，並將它貼到 [**執行**] 對話方塊中，然後在結尾輸入可執行檔的名稱。 這只是有點簡單的輸入，但有相同的結果。

[回去。](#run-your-code-in-a-command-window)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
