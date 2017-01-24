---
title: "Icons and Cursors: Image Resources for Display Devices (Image Editor for Icons) | Microsoft Docs"
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
  - "vc.editors.icon"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cursors [C++], creating"
  - "image resources, display devices"
  - "icons [C++], creating"
  - "cursors [C++], types"
  - "icons [C++]"
  - "Image editor [C++], icons and cursors"
  - "cursors [C++]"
  - "display devices, creating icons for"
  - "cursors [C++], hot spots"
  - "icons [C++], types"
ms.assetid: 8f0809a8-0cf0-4da9-b23d-51f28bf15f5b
caps.latest.revision: 15
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Icons and Cursors: Image Resources for Display Devices (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

圖示和游標為圖形化資源，可包含不同類型之顯示裝置的多種影像 \(不同的大小和色彩配置\)。 此外，游標具有「作用點」\(hot spot\)，Windows 會用它來追蹤游標的位置。 您可以使用影像編輯器來建立及編輯圖示和游標，就像是點陣圖和其他影像一樣。  
  
 當您建立新的圖示或游標時，影像編輯器會先建立一個標準類型的影像， 而且一開始會以螢幕 \(透明\) 色彩填滿影像。 如果影像是游標，其作用點一開始會在左上角 \(座標 0,0\)。  
  
 根據預設，影像編輯器可以為下表所示的裝置建立其他影像。 您可以在 \[自訂影像\][](../mfc/custom-image-dialog-box-image-editor-for-icons.md "Custom Image Dialog Box (Image Editor for Icons)") 對話方塊中輸入寬度、高度和色彩計數等參數，為其他裝置建立影像。  
  
> [!NOTE]
>  您可以使用影像編輯器來檢視 32 位元影像，但是無法編輯這類影像。  
  
|色彩|寬度 \(像素\)|高度 \(像素\)|  
|--------|---------------|---------------|  
|單色|16|16|  
|單色|32|32|  
|單色|48|48|  
|單色|64|64|  
|單色|96|96|  
|16|16|16|  
|16|32|32|  
|16|64|64|  
|16|48|48|  
|16|96|96|  
|256|16|16|  
|256|32|32|  
|256|48|48|  
|256|64|64|  
|256|96|96|  
  
-   [建立新的裝置影像 \(圖示或游標\)](../mfc/creating-a-device-image-image-editor-for-icons.md)  
  
-   [加入不同顯示裝置的影像](../mfc/adding-an-image-for-a-different-display-device-image-editor-for-icons.md)  
  
-   [複製裝置影像](../mfc/copying-a-device-image-image-editor-for-icons.md)  
  
-   [刪除裝置影像](../mfc/deleting-a-device-image-image-editor-for-icons.md)  
  
-   [在裝置影像中建立透明或反向區域](../mfc/creating-transparent-or-inverse-regions-in-device-images.md)  
  
-   [建立 256 色圖示或游標](../mfc/creating-a-256-color-icon-or-cursor-image-editor-for-icons.md)  
  
-   [設定游標的作用點](../mfc/setting-a-cursor-s-hot-spot-image-editor-for-icons.md)  
  
 如需將資源加入 Managed 專案的相關資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。如需手動將資源檔加入 Managed 專案、存取資源、顯示靜態資源及指派資源字串給屬性的相關資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 需求  
 無  
  
## 請參閱  
 [Image Editor for Icons](../mfc/image-editor-for-icons.md)   
 [圖示](http://msdn.microsoft.com/library/windows/desktop/ms646973)   
 [游標](http://msdn.microsoft.com/library/windows/desktop/ms646970)