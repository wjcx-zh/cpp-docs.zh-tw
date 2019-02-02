---
title: 視窗窗格 (圖示影像編輯器)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.bitmap
- vc.editors.icon
helpviewer_keywords:
- graphics editor [C++]
- Image editor [C++], panes
- Image editor [C++], magnification
- grids, pixel
- pixel grid, Image editor
- Image editor [C++], pixel grid
- Image editor [C++], grid settings
- grid settings, Image editor
ms.assetid: d66ea5b3-e2e2-4fc4-aa99-f50022cc690e
ms.openlocfilehash: 72b7cf056147cdbd216d861f0e710da423951c5a
ms.sourcegitcommit: efcc8c97570ddf7631570226c700e8f6ebb6c7be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2019
ms.locfileid: "55560305"
---
# <a name="window-panes-image-editor-for-icons"></a>視窗窗格 (圖示影像編輯器)

**影像編輯器** 視窗通常會顯示映像以分隔列分隔的兩個窗格。 一個檢視是實際大小，以及其他會放大 （預設的放大係數是 6）。 這兩個窗格中的檢視會自動更新： 一個窗格中的變更會立即顯示在其他。 兩個窗格，方便您處理您的映像，您可以區分個別像素為單位，並且，在此同時，觀察 映像的 實際大小 檢視您的工作影響的放大檢視。

左的窗格會使用最多所需的空間 (最多一半**映像**視窗) 來顯示您的映像的 1:1 縮放比例檢視 （預設值）。 右窗格會顯示已縮放的影像 （預設的 6:1 縮放比例）。 您可以變更每個窗格使用縮放比例**Magnify**工具[影像編輯器工具列](../windows/toolbar-image-editor-for-icons.md)或使用的快速鍵。

您可以放大的較小的窗格**影像編輯器**視窗，並使用兩個窗格顯示的大型影像的不同區域。 您可以選取窗格內選擇它。

您可以變更窗格的相對大小的指標放在分割列上，並將在分割列移至右或向左。 在分割列可以移動到任一端，如果您想要使用一個窗格。

如果**影像編輯器**窗格放大 4 倍以上，您可以顯示分隔映像中的個別像素的像素格線。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="to-change-the-magnification-factor"></a>若要變更縮放比例

根據預設，**映像**編輯器的實際大小的左窗格中顯示的檢視，和 6 在右窗格中的檢視時間的實際大小。 縮放比例倍數 （如在工作區底部的 [狀態] 列所示） 是映像的實際大小和顯示的大小之間的比例。 預設的因數為 6，範圍是從 1 到 10。

1. 選取 **影像編輯器**窗格中您想要變更其縮放比例。

1. 在 [影像編輯器 工具列](../windows/toolbar-image-editor-for-icons.md)，選取右邊的箭號[放大工具](../windows/toolbar-image-editor-for-icons.md)和從子功能表中選取 縮放比例：**1 X**， **2 X**， **6 X**，或**8 X**。

   > [!NOTE]
   > 若要選取以外所列的縮放比例**Magnify**工具中，使用的快速鍵。

## <a name="to-display-or-hide-the-pixel-grid"></a>若要顯示或隱藏像素格線

針對所有**影像編輯器**4 或更高的縮放比例的窗格，您可以顯示分隔映像中的個別像素格線。

1. 在 **映像**功能表上，選取**格線設定**。

1. 選取 [**像素格線**顯示方格中，或清除此方塊可隱藏方格] 核取方塊。

> [!TIP]
> 將游標停留在工具列按鈕時，就會出現工具提示。 這些提示可協助您識別每個按鈕的功能。

## <a name="requirements"></a>需求

無

## <a name="see-also"></a>另請參閱

[快速鍵](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[圖示影像編輯器](../windows/image-editor-for-icons.md)