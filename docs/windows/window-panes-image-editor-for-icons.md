---
title: 視窗窗格 (圖示影像編輯器)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.bitmap
- vc.editors.icon
helpviewer_keywords:
- graphics editor [C++]
- Image editor [C++], panes
ms.assetid: d66ea5b3-e2e2-4fc4-aa99-f50022cc690e
ms.openlocfilehash: f29766095048e4e06d16d37f2792ab18282eadf0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50474330"
---
# <a name="window-panes-image-editor-for-icons"></a>視窗窗格 (圖示影像編輯器)

**影像編輯器** 視窗通常會顯示映像以分隔列分隔的兩個窗格。 一個檢視是實際大小，以及其他會放大 （預設的放大係數是 6）。 這兩個窗格中的檢視會自動更新： 一個窗格中的變更會立即顯示在其他。 兩個窗格，方便您處理您的映像，您可以區分個別像素為單位，並且，在此同時，觀察 映像的 實際大小 檢視您的工作影響的放大檢視。

左的窗格會使用最多所需的空間 (最多一半**映像**視窗) 來顯示您的映像的 1:1 縮放比例檢視 （預設值）。 右窗格會顯示已縮放的影像 （預設的 6:1 縮放比例）。 您可以[變更縮放比例](../windows/changing-the-magnification-factor-image-editor-for-icons.md)中每個窗格使用**Magnify**工具[影像編輯器工具列](../windows/toolbar-image-editor-for-icons.md)或使用的快速鍵。

您可以放大的較小的窗格**影像編輯器**視窗，並使用兩個窗格顯示的大型影像的不同區域。 按一下以選取窗格中。

您可以變更窗格的相對大小的指標放在分割列上，並將在分割列移至右或向左。 在分割列可以移動到任一端，如果您想要使用一個窗格。

如果**影像編輯器** 窗格會放大 4 倍以上，您可以[顯示像素格線](../windows/displaying-or-hiding-the-pixel-grid-image-editor-for-icons.md)，用來分隔個別的像素映像中。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

無

## <a name="see-also"></a>另請參閱

[快速鍵](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[圖示影像編輯器](../windows/image-editor-for-icons.md)