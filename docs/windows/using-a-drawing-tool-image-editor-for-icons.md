---
title: 使用繪圖工具 （圖示影像編輯器） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.image.drawing
dev_langs:
- C++
helpviewer_keywords:
- Image editor [C++], selecting drawing tools
- Image editor [C++], toolbar
- drawing tools
ms.assetid: 1f8c6eef-7760-45a9-a5cb-9e15c6f91245
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8345829e5d561ead3be0052770e022f704eabc3b
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39646120"
---
# <a name="using-a-drawing-tool-image-editor-for-icons"></a>使用繪圖工具 (圖示影像編輯器)
影像編輯器的徒手繪製和清除的工具的運作方式相同： 您選取的工具，而如果有必要，請[選取前景和背景色彩](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md)和大小和形狀的選項。 然後將指標移至映像並按一下或拖曳來繪製及清除。  
  
 當您選取**橡皮擦**工具**筆刷**工具，或**噴槍**選項選取器 工具，會顯示該工具的選項。  
  
> [!TIP]
>  而不是使用**橡皮擦**工具，您可能會發現它更方便地與其中一個繪圖工具的背景色彩繪製。  
  
 您可以選取繪圖工具**影像編輯器**工具列或**映像**功能表。  
  
### <a name="to-select-and-use-a-drawing-tool-from-the-image-editor-toolbar"></a>選取並使用提供的影像編輯器 工具列上的繪圖工具  
  
1.  按一下按鈕**影像編輯器**工具列。  
  
    -   **橡皮擦**工具內目前的背景色彩與影像的繪製，當您按下滑鼠左的按鈕。  
  
    -   **鉛筆**工具手繪繪製一個像素的固定寬度。  
  
    -   **選項選取器判斷筆刷工具的形狀和大小**。  
  
    -   **噴槍**工具隨機色彩周圍散佈像素的筆刷的中心。  
  
        > [!TIP]
        >  當您將游標停留在按鈕上時，會出現工具提示[影像編輯器工具列](../windows/toolbar-image-editor-for-icons.md)。 這些提示可幫助您識別以下提及的按鈕。  
  
2.  如有必要，選取 色彩和筆刷：  
  
    -   在 [色彩調色盤](../windows/colors-window-image-editor-for-icons.md)，按一下滑鼠左的按鈕來選取前景色彩或以滑鼠右鍵按鈕以選取 背景色彩。  
  
    -   在 [選項選取器](../windows/toolbar-image-editor-for-icons.md)，按一下代表您想要使用的筆刷的形狀。  
  
3.  指向您要在繪製的影像上繪製位置。 根據您所選取的工具指標變更形狀。  
  
4.  按下滑鼠左的按鈕 （適用於的前景色彩） 或 （適用於背景色彩），以滑鼠右鍵按鈕並按住不動做為您繪製。  
  
### <a name="to-select-and-use-a-drawing-tool-from-the-image-menu"></a>選取並使用 [影像] 功能表的繪圖工具  
  
1.  按一下 **映像**功能表，然後選取**工具**命令。  
  
2.  在階層式 子功能表中，選擇您想要使用的工具。  
  
 如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。  
  
## <a name="requirements"></a>需求  
 無  
  
## <a name="see-also"></a>另請參閱  
 [快速鍵](../windows/accelerator-keys-image-editor-for-icons.md)   
 [編輯圖形資源](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [圖示影像編輯器](../windows/image-editor-for-icons.md)   
 [使用色彩](../windows/working-with-color-image-editor-for-icons.md)