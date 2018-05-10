---
title: 使用色彩 （圖示影像編輯器） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.image.color
dev_langs:
- C++
helpviewer_keywords:
- images [C++], background colors
- Image editor [C++], Colors Palette
- colors [C++], image
- Colors Palette, Image editor
- palettes, Image editor colors
- foreground colors, Image editor
- colors [C++]
ms.assetid: d34ff96f-241d-494f-abdd-13811ada8cd3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1f9016e36ce6b081446a00136445fd7ebdd5a341
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="working-with-color-image-editor-for-icons"></a>使用色彩 (圖示影像編輯器)
影像編輯器包含許多功能，特別是處理及自訂色彩。 您可以設定前景或背景色彩、 界限的區域填滿色彩，或選取要做為目前的前景或背景色彩映像上的色彩。 您可以使用工具在[影像編輯器工具列](../windows/toolbar-image-editor-for-icons.md)以及色彩調色盤中[色彩視窗](../windows/colors-window-image-editor-for-icons.md)建立映像。  
  
 所有單色及 16 色影像的色彩會都顯示在調色盤色彩 視窗中。 除了 16 個標準色彩，您可以建立您自己自訂的色彩。 色彩調色盤中的任何變更會立即變更映像中對應的色彩。  
  
 當使用 256 色圖示和游標影像中的色彩屬性[屬性 視窗](/visualstudio/ide/reference/properties-window)用。 如需詳細資訊，請參閱[建立 256 色圖示或游標](creating-a-256-color-icon-or-cursor-image-editor-for-icons.md)。  
  
> [!NOTE]
>  您可以使用影像編輯器來檢視 32 位元影像，但是無法編輯這類影像。  
  
 也可以建立全彩映像。 不過，則為 true 的色彩範例未出現在完整的調色盤，在 [色彩] 視窗中;它們只能在前景或背景色彩指示器區域中會出現。 使用所建立，則為 true 的色彩[自訂色彩選取器對話方塊](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md)。 如需詳細資訊，請參閱[自訂或變更色彩](../windows/customizing-or-changing-colors-image-editor-for-icons.md)。  
  
 可以儲存在磁碟上的自訂的色彩調色盤，並視需要重新載入。 您最近使用的色彩調色盤會儲存在登錄中，並自動載入 下一次啟動 Visual Studio。  
  
-   [選取前景或背景色彩](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md)  
  
-   [填滿色彩與影像的封閉的區域](../windows/filling-a-bounded-area-of-an-image-with-a-color-image-editor-for-icons.md)  
  
-   [中揀選色彩從映像以用於他處](../windows/picking-up-a-color-from-an-image-to-use-elsewhere-image-editor-for-icons.md)  
  
-   [選擇透明或不透明背景](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)  
  
-   [反轉選取範圍內的色彩](../windows/inverting-the-colors-in-a-selection-image-editor-for-icons.md)  
  
-   [自訂或變更色彩](../windows/customizing-or-changing-colors-image-editor-for-icons.md)  
  
-   [儲存及載入不同的調色盤](../windows/saving-and-loading-different-color-palettes-image-editor-for-icons.md)  
  
-   [色彩視窗](../windows/colors-window-image-editor-for-icons.md)  
  
 如需將資源加入至 managed 專案的詳細資訊，請參閱[桌面應用程式中的資源](/dotnet/framework/resources/index)中 *.NET Framework 開發人員手冊 》。* 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理應用程式的資源上的資訊，請參閱[全球化和當地語系化的.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。  
  
## <a name="requirements"></a>需求  
 無  
  
## <a name="see-also"></a>另請參閱  
 [快速鍵](../windows/accelerator-keys-image-editor-for-icons.md)   

