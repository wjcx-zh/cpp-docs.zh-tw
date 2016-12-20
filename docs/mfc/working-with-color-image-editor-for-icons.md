---
title: "Working with Color (Image Editor for Icons) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.image.color"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "images [C++], background colors"
  - "Image editor [C++], Colors Palette"
  - "colors [C++], image"
  - "Colors Palette, Image editor"
  - "palettes, Image editor colors"
  - "foreground colors, Image editor"
  - "colors [C++]"
ms.assetid: d34ff96f-241d-494f-abdd-13811ada8cd3
caps.latest.revision: 11
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Working with Color (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

影像編輯器包含許多專門處理及自訂色彩的功能。  您可設定前景或背景色彩、以色彩填滿封閉區域，或選取影像上的色彩用來做為前景或背景色彩。  您可使用[影像編輯器工具列](../mfc/toolbar-image-editor-for-icons.md)上的工具搭配[色彩視窗](../windows/colors-window-image-editor-for-icons.md)中的調色盤來建立影像。  
  
 單色及 16 色影像的所有色彩會顯示在 \[色彩\] 視窗中的調色盤內。  除了 16 個標準色彩之外，您還可建立您自己的自訂色彩。  變更調色盤內的任何色彩將會立即變更影像內的對應色彩。  
  
 在使用 256 色圖示和游標影像時，會使用[屬性視窗](../Topic/Properties%20Window.md)中的色彩屬性。  如需詳細資訊，請參閱[建立 256 色圖示或游標](../mfc/creating-a-256-color-icon-or-cursor-image-editor-for-icons.md)。  
  
> [!NOTE]
>  您可以使用影像編輯器來檢視 32 位元影像，但是無法編輯這類影像。  
  
 也可建立全彩影像。  不過，全彩範例不會出現在 \[色彩\] 視窗中的完整調色盤內；它們僅出現在前景或背景色彩指示器區域內。  全彩是使用[自訂色彩選取器對話方塊](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md)建立。  如需詳細資訊，請參閱[自訂或變更色彩](../windows/customizing-or-changing-colors-image-editor-for-icons.md)。  
  
 您可將自訂的調色盤儲存在磁碟上，然後在需要時重新加以載入。  您最近使用的調色盤會儲存在暫存器中，並在下次您啟動 Visual Studio 時自動載入。  
  
-   [選取前景或背景色彩](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md)  
  
-   [以色彩填滿影像的封閉區域](../windows/filling-a-bounded-area-of-an-image-with-a-color-image-editor-for-icons.md)  
  
-   [從影像中揀選色彩以用於他處](../windows/picking-up-a-color-from-an-image-to-use-elsewhere-image-editor-for-icons.md)  
  
-   [選擇透明或不透明背景](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)  
  
-   [反轉選取範圍內的色彩](../windows/inverting-the-colors-in-a-selection-image-editor-for-icons.md)  
  
-   [自訂或變更色彩](../windows/customizing-or-changing-colors-image-editor-for-icons.md)  
  
-   [儲存及載入不同的調色盤](../windows/saving-and-loading-different-color-palettes-image-editor-for-icons.md)  
  
-   [色彩視窗](../windows/colors-window-image-editor-for-icons.md)  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 需求  
 None  
  
## 請參閱  
 [Accelerator Keys](../mfc/accelerator-keys-image-editor-for-icons.md)   
 [資源](_win32_Resources)