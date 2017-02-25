---
title: "Selecting an Area of an Image (Image Editor for Icons) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.image.editing"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Image editor [C++], image selection"
  - "Image editor [C++], selecting images"
  - "images [C++], selecting"
  - "cursors [C++], selecting areas of"
ms.assetid: 8b6ce4ad-eba1-4ece-86ba-cea92c3edff2
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Selecting an Area of an Image (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可使用選取工具來定義您要剪下、複製、清除、調整大小、反轉或移動的影像範圍。  利用**矩形選取範圍**工具，可以定義及選取影像的矩形範圍。  **利用非標準的選取範圍**工具，您可徒手繪製一個外框範圍，進行剪下、複製或其他想要的作業。  
  
> [!NOTE]
>  請參閱[影像編輯器工具列](../mfc/toolbar-image-editor-for-icons.md)中所示的 \[矩形選取範圍\] 和 \[非標準的選取範圍\] 工具，或檢視與 \[影像編輯器\] 工具列上的每一個按鈕關聯的工具提示。  
  
 您也可以從選取範圍建立自訂筆刷。  如需詳細資訊，請參閱[建立自訂筆刷](../mfc/creating-a-custom-brush-image-editor-for-icons.md)。  
  
### 若要選取影像的範圍  
  
1.  在 \[影像編輯器\] 工具列上 \(或自 \[影像\] 功能表中的 \[工具\] 命令\)，按一下想要的選取範圍工具。  
  
2.  將插入點移至您要選取之影像範圍的其中一個角落。  當插入點落在影像上時，即出現十字型游標。  
  
3.  將插入點拖曳至您要選取之範圍的相對角落。  一個矩形即顯示將會選取哪些像素。  在該矩形內的所有像素 \(包括在矩形下方的像素\) 都會包含在選取範圍內。  
  
4.  放開滑鼠按鈕。  選取框線即含括所選取的範圍。  
  
### 若要選取整個影像  
  
1.  按一下目前選取範圍外的影像。  選取框線即變更焦點 \(Focus\) 並再度內含整個影像。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 需求  
  
 None  
  
## 請參閱  
 [Accelerator Keys](../mfc/accelerator-keys-image-editor-for-icons.md)   
 [Editing Graphical Resources](../mfc/editing-graphical-resources-image-editor-for-icons.md)   
 [Image Editor for Icons](../mfc/image-editor-for-icons.md)