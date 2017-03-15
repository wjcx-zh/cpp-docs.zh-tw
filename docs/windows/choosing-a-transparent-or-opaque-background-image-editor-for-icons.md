---
title: "Choosing a Transparent or Opaque Background (Image Editor for Icons) | Microsoft Docs"
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
  - "opaque backgrounds"
  - "background colors, images"
  - "colors [C++], image"
  - "Image editor [C++], transparent or opague backgrounds"
  - "background images"
  - "images [C++], transparency"
  - "images [C++], opaque background"
  - "transparent backgrounds"
  - "transparency, background"
  - "transparent backgrounds, images"
ms.assetid: 61b743d9-c86b-405d-9a81-0806431b4363
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Choosing a Transparent or Opaque Background (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當您從影像中移動或複製選取範圍時，依預設，該選取範圍內任何符合目前背景色彩的像素都是透明的；它們不會隱藏目標位置中的像素。  
  
 您可從透明背景 \(預設設定\) 切換至不透明背景，然後重新回復。  當您使用選取工具時，\[透明背景\] 和 \[不透明背景\] 選項會出現在 \[影像編輯器\] 工具列上的 \[選項\] 選取器中 \(如下所示\)。  
  
 ![背景選項 &#45; 不透明或透明](../windows/media/vcimageeditoropaqtranspback.png "vcImageEditorOpaqTranspBack")  
影像編輯器工具列上的透明和不透明選項  
  
### 在透明與不透明背景之間切換  
  
1.  在 \[影像編輯器\] 工具列中，按一下 \[選項\] 選取器，然後按一下適當的背景：  
  
    -   **不透明背景**：現有的影像會被選取範圍的所有部分隱藏。  
  
    -   **透明背景**：現有的影像會顯示穿過選取範圍內符合目前背景色彩的部分。  
  
 \-或\-  
  
-   在 \[影像\] 功能表上，選取或清除 \[不透明處理\]。  
  
 您可在選取範圍生效的同時變更背景色彩，以變更影像透明的部分。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 需求  
  
 None  
  
## 請參閱  
 [Accelerator Keys](../mfc/accelerator-keys-image-editor-for-icons.md)   
 [Working with Color](../mfc/working-with-color-image-editor-for-icons.md)