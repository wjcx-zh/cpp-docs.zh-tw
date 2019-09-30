---
title: 在 Visual Studio C++中設定您的編碼喜好設定
ms.description: Customize C++ formatting, colors, layout, line numbers, menus and more in the Visual Studio IDE.
ms.topic: overview
ms.date: 09/27/2019
ms.openlocfilehash: 90c9f39135b90a2c5015861a78dd8760b9a8aeed
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/30/2019
ms.locfileid: "71686884"
---
# <a name="set-your-c-coding-preferences-in-visual-studio"></a>在 Visual Studio C++中設定您的編碼喜好設定

您可以藉由C++個人化 Visual Studio，讓您的程式碼撰寫體驗更方便、更具生產力和 pleasurable。 您可以自訂功能表和工具列、排列視窗配置、設定色彩主題、指定C++格式規則，包括幾種 ClangFormat，以及建立自訂鍵盤快速鍵。 您可以在多部電腦之間同步處理您的喜好設定，以及建立和儲存多組喜好設定，並與小組共用。 您可以從 Visual Studio Marketplace 安裝延伸模組，以提供額外的自訂行為。 其中有許多選項都記載[于 [個人化] VISUAL STUDIO IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。

## <a name="arrange-window-layout"></a>排列視窗版面配置

在 [Visual Studio] 視窗內，空間會分成主功能表、工具列、程式碼編輯器（或文件視窗）和工具視窗（**方案總管**、**錯誤清單**等等）。 有些視窗會在同一個位置彼此重迭。 例如，**方案總管**、**類別檢視**、**資源檢視**和**原始檔控制總管**全都共用相同的預設位置。 您可以按一下畫面底部的索引標籤，在兩者之間切換。 若要同時顯示兩個以上的視窗，只要將其標題列拖曳到新的位置即可。 您可以將它固定在其中一個 Visual Studio 主視窗框線中，或將其浮動。 下圖顯示從 [程式碼編輯器] 左邊的預設位置拖曳至新停駐位置的 [ **Team Explorer** ] 視窗。 藍色陰影區域會顯示放開滑鼠按鍵時，視窗的放置位置。

![修改視窗版面配置](media/window-layout-move-team-explorer.png)

在文件視窗中，每個開啟的檔案都包含在索引標籤式框架中。 您可以將這些索引標籤浮動或鎖定，就像工具視窗一樣。 如需詳細資訊，請參閱[在 Visual Studio 中自訂視窗版面配置](/visualstudio/ide/customizing-window-layouts-in-visual-studio)。

若要隱藏所有工具視窗並最大化 [程式碼編輯器] 視窗，請按**Alt** + **Shift** + **Enter**切換*全螢幕模式*。

## <a name="set-c-coding-styles-and-formatting"></a>設定C++編碼樣式和格式

您可以藉由流覽至 [**工具**] [ > **選項**]，以指定許多個別的程式碼格式化選項，例如縮排和大括弧位置  > **文字編輯器** > **C/C++**  > **格式**（或輸入**Ctrl + Q**並搜尋「格式」）。 或者，您可以指定其中一個[ClangFormat](https://clang.llvm.org/docs/ClangFormat.html)樣式（或您自己的自訂 ClangFormat 樣式）：

![ClangFormat 選項](media/clang-format-ide.png)

如需所有格式選項的詳細資訊，請參閱[選項、文字編輯器、CC++/、格式](/visualstudio/ide/reference/options-text-editor-c-cpp-formatting)。

## <a name="set-the-color-theme"></a>設定色彩佈景主題

若要設定淺色或深色背景，請輸入**Ctrl + Q**並搜尋「色彩主題」。 您也可以透過 [**工具**]  > **選項** > **環境**中取得，然後選擇 [**色彩主題**]：

![色彩主題](media/tools-options-color-theme.png)

下圖顯示深色主題：

![暗色調佈景主題](media/tools-options-dark-theme.png)

## <a name="customize-code-colorization"></a>自訂程式碼顏色標示

在 Visual Studio 2019 中，您可以從三個預先定義的*色彩*配置中選擇，以指定如何在編輯器中以色彩標示程式碼元素。 若要選擇主題，請流覽至 **工具**  > **選項**  > **文字編輯器**  > **C/C++**  > **視圖**，然後選擇 **色彩配置**：

![C++色彩配置](media/color-schemes.png)

在 [ **Visual Studio 2017**色彩配置] 中，大部分的程式碼元素只是黑色。 在**增強型**色彩配置中，會以色彩標示函數、區域變數、宏和其他元素。 在 **Enhanced （Globals 與成員）**  配置、全域函式和變數以色彩標示，以與類別成員對比。 預設模式已**增強**，而且看起來像這樣：

![增強的色彩配置](media/color-scheme-enhanced.png)

不論哪一個主題或色彩配置為作用中，您都可以流覽至 **工具**  > **選項**  >  @no__t**環境**中，自訂個別程式碼元素**的字型和色彩（或**輸入**Ctrl + Q**並搜尋「字型」）。 向下查看顯示專案的清單，直到您看到C++選項：

![C++字型和色彩選項](media/tools-options-cpp-colors.png)

您在此設定的色彩會覆寫針對色彩配置所定義的值。 如果您變更了色彩，但想要使用色彩配置的預設色彩，就必須將它設回**預設值**。

## <a name="customize-the-toolbars"></a>自訂工具列

工具列提供一個便利的方式，只要按一下滑鼠按鍵就可以發出命令，而不是使用功能表或鍵盤快速鍵。 Visual Studio 包含一組標準的工具列。 針對標準C++開發，最有用的工具列可能是標準、文字編輯器、組建、Debug、原始檔控制，而且可能比較檔案。 對於 Windows 開發，對話方塊編輯器和影像編輯器適用于配置對話方塊和編輯圖示。

將滑鼠停留在工具列中的圖示上，以查看它代表的命令：

![工具列 QuickInfo](media/toolbar-mouse-hover.png)

您可以按一下向下箭號來新增或移除命令，或建立自訂工具列。 若要將工具列移到新的位置，請將它拖曳到左邊的虛線列上：

![自訂或移動工具列](media/toolbar-move-edit.png).

如需詳細資訊，請參閱[如何：在 Visual Studio @ no__t-0 中自訂功能表和工具列。

## <a name="show-or-hide-line-numbers"></a>顯示或隱藏行號

若要指定行號是否顯示在編輯器視窗的左邊，請流覽至並核取或取消勾選**行號**：

![行號](media/tools-options-line-numbers.png)

## <a name="create-keyboard-shortcuts"></a>建立鍵盤快速鍵

Visual Studio 中的所有命令都可以透過鍵盤快速鍵，搭配 Ctrl、Alt 和 Shift 鍵使用不同的按鍵組合來進行。 您可以建立自己的快捷方式，方法是流覽至 [**工具**] [ > ] [**選項**] [ > ] [**環境**]  > **鍵盤**（或輸入**Ctrl + Q**並搜尋「快捷方式」）。 如需詳細資訊，請參閱[在 Visual Studio 中識別及自訂鍵盤快速鍵](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio)。
