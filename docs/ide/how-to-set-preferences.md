---
title: 在視覺化工作室中設定C++編碼首選項
ms.description: Customize C++ formatting, colors, layout, line numbers, and menus in the Visual Studio IDE.
ms.topic: overview
ms.date: 09/27/2019
ms.openlocfilehash: e3a665ead7a314b343ec3320e95b189f83a38a47
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365395"
---
# <a name="set-your-c-coding-preferences-in-visual-studio"></a>在視覺化工作室中設定C++編碼首選項

通過個人化 Visual Studio,您可以使C++編碼體驗更加方便、高效和愉快。 您可以：

- 自定義功能表和工具列。
- 排列窗口佈局。
- 設置顏色主題。
- 指定C++格式設置規則,包括ClangFormat的幾種樣式。
- 創建自定義鍵盤快速鍵。

您可以在多台電腦上同步首選項,並創建和存儲多組首選項,並與團隊成員共用這些首選項集。 您可以安裝 Visual Studio 應用商店中的擴展,從而提供自定義行為的其他選項。 有關詳細資訊,請參閱[個人化可視化工作室 IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。

## <a name="arrange-window-layout"></a>排列視窗佈局

在 Visual Studio 視窗中,空間分為主功能表、工具列、代碼編輯器(或文件視窗)和工具視窗(如解決方案資源管理器和錯誤清單)。 某些視窗在同一位置相互重疊。 例如,解決方案資源管理器、類檢視、資源檢視和原始程式碼管理資源管理員都共用相同的預設位置。 通過選擇框架底部的選項卡,您可以在它們之間切換。 要使兩個或多個視窗同時可見,只需按標題列將其中一個視窗拖動到新位置。 您可以將它停靠在 Visual Studio 主視窗邊框之一上,也可以浮動它。

以下螢幕截圖顯示**Team Explorer**視窗從預設位置拖動到代碼編輯器左側的新停靠位置。 藍色陰影區域顯示釋放滑鼠按鈕時視窗的位置。

![視覺化工作室團隊資源管理器視窗的螢幕截圖,突顯佈局更改](media/window-layout-move-team-explorer.png)

在文件視窗中,每個打開的檔都包含在選項卡式框架中。 您可以浮動或鎖定這些選項卡,就像工具視窗一樣。 有關詳細資訊,請參閱[在可視化工作室中自定義視窗佈局](/visualstudio/ide/customizing-window-layouts-in-visual-studio)。

要隱藏所有工具視窗並最大化代碼編輯器視窗,請按**Alt** + **Shift** + **Enter**切換*全螢幕模式*。

## <a name="set-c-coding-styles-and-formatting"></a>設定C++編碼樣式和格式

您可以指定許多單獨的程式碼格式設定選項,如縮進和大括弧位置。 為此,轉到**工具** > **選項** > **文字編輯器** > **C/C++** > **格式**(或鍵入**Ctrl + Q**並搜尋"格式" 或者,您可以指定一種[ClangFormat 樣式](https://clang.llvm.org/docs/ClangFormat.html)(或您自己的自訂 ClangFormat 樣式)。

![Clang格式選項的螢幕擷取](media/clang-format-ide.png)

關於所有格式選項的詳細資訊,請參考[選項、文字編輯器、C/C++、格式化](/visualstudio/ide/reference/options-text-editor-c-cpp-formatting)。

## <a name="set-the-color-theme"></a>設定色彩佈景主題

要設置淺色或深色背景,鍵入**Ctrl + Q**並搜索"顏色主題"。 您還可以**透過工具** > **選項** > **環境**來找到這些,並選擇**顏色主題**。

![顏色主題的螢幕擷取](media/tools-options-color-theme.png)

例如,下面是深色主題:

![帶有深色主題的視覺工作室的螢幕截圖](media/tools-options-dark-theme.png)

## <a name="customize-code-colorization"></a>自訂代碼著色

從 Visual Studio 2019 中,您可以從三個預先定義的*顏色機制中*選擇 。 這些指定代碼元素在編輯器中的著色方式。 要選擇主題,請轉到**工具** > **選項** > **文字編輯器** > **C/C++** > **檢視**,然後選擇 **「顏色機制**」:

![C++色彩配置選項的螢幕截圖,並突出顯示增強](media/color-schemes.png)

在名為 Visual **Studio 2017**的色彩配置中,大多數代碼元素只是黑色。 在**增強**色彩配置中,函數、局部變數、宏和其他元素被著色。 在**增強(全域與成員)** 方案中,全域函數和變數的顏色與類成員進行對比。 預設模式為**增強**,如下所示:

![增強顏色機制的螢幕擷圖](media/color-scheme-enhanced.png)

無論哪個主題或色彩配置處於活動狀態,都可以自定義各個代碼元素的字體和顏色。 為此,轉到**工具** > **選項** > **環境** > **字型和顏色**(或鍵入**Ctrl + Q**並搜索"字型" 向下滾動顯示項清單,直到看到C++選項。

![C++字型與顏色選項的螢幕擷取](media/tools-options-cpp-colors.png)

此處設置的顏色將覆蓋為色彩配置定義的值。 如果要傳回顏色機制的預設顏色,將顏色設定回**預設**。

## <a name="customize-the-toolbars"></a>自訂工具列

工具列提供了一種只需單擊即可發出命令的便捷方法,而不是使用菜單或鍵盤快捷鍵。 Visual Studio 包含一組標準工具列。 對於標準C++開發,最有用的工具列可能是標準、文本編輯器、生成、調試、原始程式碼控制和比較檔。 對於 Windows 開發,對話方塊編輯器和圖像編輯器可用於佈局對話方塊和編輯圖示。

將滑鼠懸停在工具列中的圖示上,以查看它表示的命令:

![工具列圖示的螢幕截圖,以及懸停時可用的命令資訊範例](media/toolbar-mouse-hover.png)

您可以通過選擇向下箭頭來添加或刪除命令或創建自訂工具列。 要將工具列移動到新位置,請將其拖動到左側的虛線。

![工具列的螢幕截圖,下箭頭和虛線突出顯示](media/toolbar-move-edit.png).

有關詳細資訊,請參閱[如何:在 Visual Studio 中自訂選單和工具列](/visualstudio/ide/how-to-customize-menus-and-toolbars-in-visual-studio)。

## <a name="show-or-hide-line-numbers"></a>顯示或隱藏列號

您可以指定行號是否顯示在編輯器視窗的左側。 在**選項**中,**在 C/C++** 下,選擇 **「一般**」 。 在 **「設定」** 部份中,根據您的偏好選擇或清除**列號**。

![常規選項的螢幕截圖,突顯行號](media/tools-options-line-numbers.png)

## <a name="create-keyboard-shortcuts"></a>建立鍵盤捷徑

Visual Studio 中的許多命令都有*鍵盤快速鍵*、鍵組合和 Ctrl、Alt 和 Shift 鍵。 您可以在 Visual Studio 中修改這些鍵盤快捷鍵或創建自己的鍵盤快捷鍵。 跳到**工具** > **選項** > **Environment**環境 > **鍵盤**(或鍵入**Ctrl + Q**並搜尋"快速方式" 有關詳細資訊,請參閱在[Visual Studio 中識別和自訂鍵盤快捷方式](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio)。
