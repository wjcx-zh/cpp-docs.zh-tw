---
title: 在 Visual Studio C++中設定您的編碼喜好設定
ms.description: Customize C++ formatting, colors, layout, line numbers, and menus in the Visual Studio IDE.
ms.topic: overview
ms.date: 09/27/2019
ms.openlocfilehash: f1d222dc38720ea897cfbf2fb9fa0dd2727e7720
ms.sourcegitcommit: 4517932a67bbf2db16cfb122d3bef57a43696242
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2019
ms.locfileid: "71816565"
---
# <a name="set-your-c-coding-preferences-in-visual-studio"></a>在 Visual Studio C++中設定您的編碼喜好設定

您可以藉由C++個人化 Visual Studio，讓您的程式碼撰寫體驗更方便、更具生產力，並 pleasurable。 您可以：

- 自訂功能表和工具列。
- 排列視窗版面配置。
- 設定色彩主題。
- 指定C++格式規則，包括數種 ClangFormat 樣式。
- 建立自訂鍵盤快速鍵。

您可以在多部電腦之間同步處理您的喜好設定，以及建立和儲存多組喜好設定，並與小組共用。 您可以從 Visual Studio Marketplace 安裝延伸模組，為您提供自訂行為的其他選項。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。

## <a name="arrange-window-layout"></a>排列視窗版面配置

在 [Visual Studio] 視窗內，空間會分成主功能表、工具列、程式碼編輯器（或文件視窗）和工具視窗（例如方案總管和錯誤清單）。 有些視窗會在同一個位置彼此重迭。 例如，方案總管、類別檢視、資源檢視和原始檔控制總管全都共用相同的預設位置。 您可以選取框架底部的索引標籤，在其中切換。 若要同時顯示兩個以上的視窗，只要將其標題列拖曳到新的位置即可。 您可以將它固定在其中一個 Visual Studio 主視窗框線中，或將其浮動。

下列螢幕擷取畫面顯示將 [ **Team Explorer** ] 視窗從其預設位置拖曳至程式碼編輯器左側的新固定位置。 藍色陰影區域會顯示放開滑鼠按鍵時，視窗的放置位置。

![Visual Studio Team Explorer 視窗的螢幕擷取畫面，其中已反白顯示版面配置變更](media/window-layout-move-team-explorer.png)

在文件視窗中，每個開啟的檔案都包含在索引標籤式框架中。 您可以浮動或鎖定這些索引標籤，就像工具視窗一樣。 如需詳細資訊，請參閱[在 Visual Studio 中自訂視窗版面配置](/visualstudio/ide/customizing-window-layouts-in-visual-studio)。

若要隱藏所有工具視窗並最大化 [程式碼編輯器] 視窗，請按**Alt** + **Shift** + **Enter**切換*全螢幕模式*。

## <a name="set-c-coding-styles-and-formatting"></a>設定C++編碼樣式和格式

您可以指定許多個別的程式碼格式化選項，例如縮排和大括弧位置。 若要這麼做，請移至 [**工具**]  > **選項** > **文字編輯器** > **C/C++**  > **格式**（或輸入**Ctrl + Q**並搜尋「格式」）。 或者，您可以指定其中一個[ClangFormat](https://clang.llvm.org/docs/ClangFormat.html)樣式（或您自己的自訂 ClangFormat 樣式）。

![ClangFormat 選項的螢幕擷取畫面](media/clang-format-ide.png)

如需所有格式選項的詳細資訊，請參閱[選項、文字編輯器、CC++/、格式](/visualstudio/ide/reference/options-text-editor-c-cpp-formatting)。

## <a name="set-the-color-theme"></a>設定色彩佈景主題

若要設定淺色或深色背景，請輸入**Ctrl + Q**並搜尋「色彩主題」。 您也可以前往 [**工具**] [ > ] [**選項**] [ > ]**環境**，然後選擇 [**色彩主題**] 來尋找這些方法。

![色彩主題的螢幕擷取畫面](media/tools-options-color-theme.png)

例如，以下是深色主題：

![具有深色色彩主題之 Visual Studio 的螢幕擷取畫面](media/tools-options-dark-theme.png)

## <a name="customize-code-colorization"></a>自訂程式碼顏色標示

在 Visual Studio 2019 中，您可以選擇三種預先定義的*色彩*配置。 這些會指定如何在編輯器中以色彩標示程式碼元素。 若要選擇主題，請移至 **工具**  > **選項**  > **文字編輯器**  > **C/C++**  > **視圖**，然後選擇 **色彩配置**：

![色彩配置C++選項的螢幕擷取畫面，並反白顯示增強型](media/color-schemes.png)

在稱為**Visual Studio 2017**的色彩配置中，大部分的程式碼專案都只是黑色。 在**增強型**色彩配置中，會以色彩標示函數、區域變數、宏和其他元素。 在 **Enhanced （Globals 與成員）**  配置、全域函式和變數以色彩標示，以與類別成員對比。 預設模式已**增強**，而且看起來像這樣：

![增強型色彩配置的螢幕擷取畫面](media/color-scheme-enhanced.png)

不論哪一個主題或色彩配置為作用中，您都可以自訂個別程式碼專案的字型和色彩。 若要這麼做，請移至 [**工具**]  > **選項** > **環境** >  字型**和色彩**（或是輸入**Ctrl + Q**並搜尋「字型」）。 向下查看顯示專案的清單，直到您看到C++選項為止。

![字型和C++色彩選項的螢幕擷取畫面](media/tools-options-cpp-colors.png)

您在此設定的色彩會覆寫針對色彩配置所定義的值。 如果您想要回到色彩配置的預設色彩，請將色彩設回**預設值**。

## <a name="customize-the-toolbars"></a>自訂工具列

工具列可讓您只需按一下就能發出命令，而不是使用功能表或鍵盤快速鍵。 Visual Studio 包含一組標準的工具列。 針對標準C++開發，最有用的工具列可能是標準、文字編輯器、組建、Debug、原始檔控制和比較檔案。 對於 Windows 開發，對話方塊編輯器和影像編輯器適用于配置對話方塊和編輯圖示。

將滑鼠停留在工具列中的圖示上，以查看它代表的命令：

![工具列圖示的螢幕擷取畫面，其中包含停留時可用的命令資訊範例](media/toolbar-mouse-hover.png)

您可以藉由選取向下箭號來新增或移除命令，或建立自訂工具列。 若要將工具列移到新的位置，請將它拖曳到左邊的點線上。

![工具列的螢幕擷取畫面，反白顯示向下箭號的長條線](media/toolbar-move-edit.png).

如需詳細資訊，請參閱[如何：在 Visual Studio @ no__t-0 中自訂功能表和工具列。

## <a name="show-or-hide-line-numbers"></a>顯示或隱藏行號

您可以指定行號是否顯示在編輯器視窗的左邊。 在 [**選項**] 的 [ **CC++/** ] 底下，選取 **[一般**]。 在 [**設定**] 區段中，選取或清除 [**行號**]，視您的偏好而定。

![一般選項的螢幕擷取畫面，其中的行號已反白顯示](media/tools-options-line-numbers.png)

## <a name="create-keyboard-shortcuts"></a>建立鍵盤快速鍵

Visual Studio 中的許多命令都有*鍵盤快速鍵*、按鍵組合和 Ctrl、Alt 和 Shift 鍵。 您可以修改這些鍵盤快速鍵，或在 Visual Studio 中建立您自己的快速鍵。 移至 [**工具**]  > **選項** > **環境** > **鍵盤**（或輸入**Ctrl + Q**並搜尋「快捷方式」）。 如需詳細資訊，請參閱[在 Visual Studio 中識別及自訂鍵盤快速鍵](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio)。
