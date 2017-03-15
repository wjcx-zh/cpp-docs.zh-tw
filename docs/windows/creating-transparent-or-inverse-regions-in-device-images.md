---
title: "Creating Transparent or Inverse Regions in Device Images (Image Editor for Icons) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "cursors [C++], screen regions"
  - "inverse colors, device images"
  - "transparent regions, device images"
  - "transparency, device images"
  - "Image editor [C++], device images"
  - "inverse regions, device images"
  - "cursors [C++], transparent regions"
  - "screen colors"
  - "regions, transparent"
  - "icons [C++], transparent regions"
  - "display devices, transparent and screen regions"
  - "transparent regions in devices"
  - "regions, inverse"
  - "colors [C++], Image editor"
  - "device projects, transparent images"
  - "icons [C++], screen regions"
ms.assetid: a994954b-b039-4391-a535-58d1fa10fc3b
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Creating Transparent or Inverse Regions in Device Images (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在[影像編輯器](../mfc/image-editor-for-icons.md)中，初始圖示或游標影像具有透明屬性。  雖然圖示和游標影像都是矩形，但是有許多都不是顯示成矩形，因為影像的一部分是透明的；螢幕上的底層影像會穿過圖示或游標顯示。  當您拖曳圖示時，影像的一部分可能會以反轉的色彩顯示。  建立這項效果的方法，是在[色彩視窗](../windows/colors-window-image-editor-for-icons.md)中設定螢幕色彩和反向色彩。  
  
 您套用至圖示及游標的螢幕和反向色彩會成為衍生影像的形狀或色彩，或指定反向區域。  該色彩指出具有那些屬性的影像部分。  您可變更代表編輯中的螢幕色彩和反向色彩屬性的色彩。  這些變更並不會影響您應用程式中的圖示或游標的外觀。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要建立透明或反向區域  
  
1.  在 \[色彩\] 視窗中，按一下 \[螢幕色彩\] 選取器或 \[反向色彩\] 選取器。  
  
2.  使用繪圖工具，將螢幕或反向色彩套用至影像。  如需繪圖工具的詳細資訊，請參閱[Using a Drawing Tool](../mfc/using-a-drawing-tool-image-editor-for-icons.md)。  
  
### 若要變更螢幕或反向色彩  
  
1.  選取 \[螢幕色彩\] 選取器或 \[反向色彩\] 選取器。  
  
2.  從 \[色彩\] 視窗中的調色盤中選擇某個**色彩**。  
  
     即自動對其他選取器指定互補色彩。  
  
    > [!TIP]
    >  如果您按兩下 \[螢幕色彩\] 或 \[反向色彩\] 選取器，即出現[自訂色彩選取器對話方塊](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md)。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 需求  
  
 None  
  
## 請參閱  
 [Accelerator Keys](../mfc/accelerator-keys-image-editor-for-icons.md)   
 [Icons and Cursors: Image Resources for Display Devices](../mfc/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)