---
title: "Changing Image Properties (Image Editor for Icons) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "images [C++], properties"
  - "Image editor [C++], Properties window"
  - "Image editor [C++], image properties"
  - "Properties window, image editor"
ms.assetid: f6172bf1-08c4-4dfd-b542-dd8749e83fe6
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Changing Image Properties (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可使用[屬性視窗](../Topic/Properties%20Window.md)來設定或修改影像的屬性。  
  
### 若要變更影像的屬性  
  
1.  在 \[影像\] 編輯器中開啟影像。  
  
2.  在 \[屬性\] 視窗中，變更影像的部分或所有屬性。  
  
    |屬性|描述|  
    |--------|--------|  
    |**Colors**|指定影像的色彩配置。  選取單色、16 或 256 色或全彩 \(True Color\)。  如果您已使用 16 色調色盤 \(Palette\) 繪製影像，則選取單色會導致影像中的色彩被黑色和白色替代。  對比並不會一直保持，例如，紅色與綠色的相鄰區域都會轉換成黑色。|  
    |**Filename**|指定影像檔名稱。  依預設，Visual Studio 會指定一個基本檔名，其指定方法為移除預設資源識別項 \(IDB\_BITMAP1\) 中的前四個字元 \("IDB\_"\)，然後加入適當的副檔名。  本例中的影像檔名將會是 BITMAP1.bmp。  您可將它重新命名為 MYBITMAP1.bmp。|  
    |**Height**|設定影像的高度 \(以像素為單位\)。  預設值為 48。  會裁剪影像，或是在現有影像的下方加入空白。|  
    |**ID**|設定資源的識別項。  根據預設，Microsoft Visual Studio 會對影像依序指定下一個可用的識別項，如 IDB\_BITMAP1、IDB\_BITMAP2，依此類推。  對圖示及游標也使用類似的命名方式。|  
    |**Palette**|變更色彩屬性。  按兩下來選取色彩及顯示[自訂色彩選取器對話方塊](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md)。  在適當的文字方塊內輸入 RGB 或 HSL 值來定義色彩。|  
    |**SaveCompressed**|指出影像是否為壓縮格式。  這個屬性是唯讀的。  Visual Studio 無法讓您以壓縮格式儲存影像，因此針對在 Visual Studio 中建立的任何影像，這個屬性將會是 **False**。  如果您在 Visual Studio 中開啟 \(以另一個程式建立的\) 壓縮影像，這個屬性將會是 **True**。  如果您使用 Visual Studio 存壓縮影像，它將會解壓縮，且這個屬性將還原成 **False**。|  
    |**Width**|設定影像的寬度 \(以像素為單位\)。  點陣圖的預設值為 48。  會裁剪影像，或是在現有影像的右邊加入空白。|  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 需求  
  
 None  
  
## 請參閱  
 [Accelerator Keys](../mfc/accelerator-keys-image-editor-for-icons.md)   
 [Editing Graphical Resources](../mfc/editing-graphical-resources-image-editor-for-icons.md)   
 [Image Editor for Icons](../mfc/image-editor-for-icons.md)