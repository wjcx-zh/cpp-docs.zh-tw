---
title: "Editing Control Properties | Microsoft Docs"
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
  - "controls [C++], undoing changes"
  - "controls [C++], editing properties"
  - "dialog box controls, editing properties"
ms.assetid: 9bdae21d-6dec-4344-a197-2ca4fc46d040
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Editing Control Properties
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

### 若要編輯控制項或屬性  
  
1.  在對話方塊中，選取您要修改的控制項。  
  
    > [!NOTE]
    >  如果您選取多個控制項，只有這些選取的控制項都共有的屬性才可以編輯。  
  
2.  在[屬性視窗](../Topic/Properties%20Window.md)中變更控制項的屬性。  
  
    > [!NOTE]
    >  如果您將按鈕、選項按鈕或核取方塊控制項的 \[點陣圖\] 屬性設為 **True**，便會為該控制項實作 BS\_BITMAP 樣式。  如需詳細資訊，請參閱[按鈕樣式](../mfc/reference/button-styles.md)。  如需使點陣圖與控制項設定產生關聯的範例，請參閱 [CButton::SetBitmap](../Topic/CButton::SetBitmap.md)。  如果您是在對話方塊資源編輯器中，點陣圖就不會出現在您的控制項。  
  
### 若要復原編輯控制項屬性的變更  
  
1.  確定控制項在對話方塊編輯器中有焦點。  
  
2.  從 \[編輯\] 功能表選擇 \[復原\] \(如果焦點不在控制項上，便沒有 \[復原\] 命令可使用\)。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 需求  
  
 Win32  
  
## 請參閱  
 [Controls in Dialog Boxes](../mfc/controls-in-dialog-boxes.md)