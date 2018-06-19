---
title: 繪製線條或封閉的圖形 （圖示影像編輯器） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- closed figures, drawing
- lines [C++], painting
- lines [C++], drawing
- Image editor [C++], drawing lines
- shapes, drawing
ms.assetid: 7edd86db-77b1-451f-8001-bbfed9c6304f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6e2defbde7963c6e58cdfe3f4a25ea550ad88e5f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33882771"
---
# <a name="drawing-lines-or-closed-figures-image-editor-for-icons"></a>繪製線條或封閉圖形 (圖示影像編輯器)
影像編輯器工具繪製線條和封閉的圖形的運作方式相同： 您將插入點放在一個點並拖曳至另一個。 程式行、 這些點是端點。 封閉圖形，這些點為對角的矩形。  
  
 線條會繪製的寬度，取決於目前的筆刷選取項目，和在寬度取決於目前的寬度選取範圍內繪製框架的數字。 線條和所有數字，同時已框架處理和填滿，會繪製在目前的前景色彩如果按下滑鼠左的按鈕，或目前的背景色彩中您按下滑鼠按鈕。  
  
### <a name="to-draw-a-line"></a>繪製線條  
  
1.  在[影像編輯器工具列](../windows/toolbar-image-editor-for-icons.md)(或從**映像**功能表上，**工具**命令)，按一下 **列**工具。  
  
2.  如有必要，選取 色彩和筆刷：  
  
    -   在[色彩調色盤](../windows/colors-window-image-editor-for-icons.md)，按一下滑鼠左鍵，選取前景色彩或滑鼠按鈕選取背景色彩。  
  
    -   在[選項選取器](../windows/toolbar-image-editor-for-icons.md)，按一下代表您想要使用的筆刷形狀。  
  
3.  將指標放在線條的起始點。  
  
4.  拖曳至線條的端點。  
  
### <a name="to-draw-a-closed-figure"></a>若要繪製封閉的圖表  
  
1.  在**影像編輯器**工具列 (或從**映像**功能表上，**工具**命令)，按一下 **封閉圖形繪製**工具。  
  
     **封閉圖形繪製**工具建立數字，其個別按鈕上所示。  
  
2.  如果有必要，請選取色彩和線條寬度。  
  
3.  將指標移至其中一個矩形區域要繪製圖形的角落。  
  
4.  將指標拖曳至對角的角落。  
  
 如需將資源加入至 managed 專案的詳細資訊，請參閱[桌面應用程式中的資源](/dotnet/framework/resources/index)中 *.NET Framework 開發人員手冊 》。* 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理應用程式的資源上的資訊，請參閱[全球化和當地語系化的.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。  
  
 需求  
  
 無  
  
## <a name="see-also"></a>另請參閱  
 [快速鍵](../windows/accelerator-keys-image-editor-for-icons.md)   
 [編輯圖形資源](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [圖示影像編輯器](../windows/image-editor-for-icons.md)   
 [使用色彩](../windows/working-with-color-image-editor-for-icons.md)

