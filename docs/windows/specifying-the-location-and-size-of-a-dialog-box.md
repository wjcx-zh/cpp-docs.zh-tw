---
title: "Specifying the Location and Size of a Dialog Box | Microsoft Docs"
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
  - "dialog boxes, size"
  - "dialog boxes, positioning"
ms.assetid: 2b7c495e-6595-4cfb-9664-80b2826d0851
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Specifying the Location and Size of a Dialog Box
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

對話方塊的位置和大小，以及內部控制項的位置和大小會以對話方塊單位測量。  當選取控制項和對話方塊時，個別控制項和對話方塊的值會出現在 Visual Studio 狀態列的右下方。  
  
 可以在[屬性視窗](../Topic/Properties%20Window.md)中設定三個屬性以指定對話方塊會在螢幕何處出現。  Center 屬性是 Boolean；如果您將值設為 True，對話方塊一定會出現在螢幕的中間。  如果設為 False，即可進一步設定 XPos 和 YPos 屬性，明確定義對話方塊會在螢幕何處出現。  位置屬性是從定義為 {X\=0, Y\=0} 的檢視區域的左上角的位移 \(Offset\) 值。  位置也是依據 **Absolute Align** 屬性：如果是 True，座標是相對於螢幕；如果是 False，座標是相對於對話方塊擁有者的視窗。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 需求  
 Win32  
  
## 請參閱  
 [Controls in Dialog Boxes](../mfc/controls-in-dialog-boxes.md)   
 [控制項](../mfc/controls-mfc.md)