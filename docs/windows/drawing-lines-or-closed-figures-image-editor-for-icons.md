---
title: 繪製線條或封閉的圖形 （圖示影像編輯器） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Image editor [C++], drawing lines
- shapes, drawing
ms.assetid: 7edd86db-77b1-451f-8001-bbfed9c6304f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c6c5652f61211ebd4d33de6f2dce07bd49b4f0a0
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44313232"
---
# <a name="drawing-lines-or-closed-figures-image-editor-for-icons"></a>繪製線條或封閉圖形 (圖示影像編輯器)

影像編輯器工具繪製線條和封閉的圖形的運作方式相同： 您將插入點放在一個點，並拖曳到另一個。 線條，這些點會是端點。 封閉圖形，這些點會是相反的邊角的矩形。

寬度取決於目前的筆刷選取範圍，以繪製線條，而且已框架處理的數字會繪製取決於目前的寬度選取範圍的寬度。 線條和所有數字，做為外框和填滿，會繪製在目前的前景色彩如果按下滑鼠左的按鈕，或目前的背景色彩如果按下滑鼠右按鈕。

### <a name="to-draw-a-line"></a>若要繪製一條線

1. 上[影像編輯器] 工具列](../windows/toolbar-image-editor-for-icons.md)(或從**映像**功能表**工具**命令)，按一下 [**列**工具。

2. 如有必要，選取 色彩和筆刷：

   - 在 [色彩調色盤](../windows/colors-window-image-editor-for-icons.md)，按一下滑鼠左的按鈕來選取前景色彩或以滑鼠右鍵按鈕以選取 背景色彩。

   - 在 [選項選取器](../windows/toolbar-image-editor-for-icons.md)，按一下代表您想要使用的筆刷的形狀。

3. 將指標放在直線的起點。

4. 拖曳以直線的端點。

### <a name="to-draw-a-closed-figure"></a>若要繪製封閉的圖表

1. 上**影像編輯器**工具列 (或從**映像**功能表**工具**命令)，按一下 **封閉圖形繪製**工具。

   **封閉圖形繪製**工具建立圖形，在其個別的按鈕上所示。

2. 如有必要，選取 色彩和線條寬度。

3. 將指標移至您要在其中繪製圖表的矩形區域的其中一個角落。

4. 將指標拖曳至 對角的角落。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

無

## <a name="see-also"></a>另請參閱

[快速鍵](../windows/accelerator-keys-image-editor-for-icons.md)  
[編輯圖形資源](../windows/editing-graphical-resources-image-editor-for-icons.md)  
[圖示影像編輯器](../windows/image-editor-for-icons.md)  
[使用色彩](../windows/working-with-color-image-editor-for-icons.md)