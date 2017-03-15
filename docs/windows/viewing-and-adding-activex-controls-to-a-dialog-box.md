---
title: "Viewing and Adding ActiveX Controls to a Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.controls.activex"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "dialog boxes [C++], adding ActiveX controls"
  - "Insert ActiveX Control command"
  - "ActiveX controls [C++], adding to dialog boxes"
ms.assetid: e1c2e3ae-e1b0-40d3-9766-623007073856
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Viewing and Adding ActiveX Controls to a Dialog Box
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual Studio 可讓您在您的對話方塊中插入 ActiveX 控制項。  
  
### 查看您可使用的 ActiveX 控制項  
  
1.  在 \[對話方塊\] 編輯器中開啟對話方塊。  
  
2.  在對話方塊主體中的任意處按一下滑鼠右鍵。  
  
3.  在捷徑功能表上，按一下 \[插入 ActiveX 控制項\]。  
  
     [&#91;插入 ActiveX 控制項&#93; 對話方塊](../mfc/insert-activex-control-dialog-box.md)會隨即出現，顯示您系統上所有的 ActiveX 控制項。 ActiveX 控制項檔案的路徑會顯示在對話方塊的底部。  
  
### 在對話方塊中加入 ActiveX 控制項  
  
1.  在 [&#91;插入 ActiveX 控制項&#93; 對話方塊](../mfc/insert-activex-control-dialog-box.md)中，選取您要加入對話方塊中的控制項，然後按一下 \[確定\]。  
  
     該控制項會出現在對話方塊中。您可以像處理其他控制項般地加以編輯，或為其建立處理常式。  
  
    > [!NOTE]
    >  您可以將 ActiveX 控制項加入 [&#91;工具箱&#93; 視窗](../Topic/Toolbox.md)。 如需詳細資訊，請參閱[管理 &#91;工具箱&#93; 中的項目和索引標籤](http://msdn.microsoft.com/zh-tw/21285050-cadd-455a-b1f5-a2289a89c4db)。  
  
    > [!CAUTION]
    >  在您的系統上散發所有的 ActiveX 控制項可能不合法。 請參閱安裝這些控制項之軟體的授權合約，或連絡軟體公司。  
  
     您可以將控制項置於 \[工具箱\] 視窗內，以便於存取。 如需詳細資訊，請參閱[自訂 &#91;工具箱&#93; 對話方塊](http://msdn.microsoft.com/zh-tw/bd07835f-18a8-433e-bccc-7141f65263bb)。  
  
 如需將資源加入 Managed 專案的相關資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。如需手動將資源檔加入 Managed 專案、存取資源、顯示靜態資源及指派資源字串給屬性的相關資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 **需求**  
  
 Win32  
  
## 請參閱  
 [Controls in Dialog Boxes](../mfc/controls-in-dialog-boxes.md)   
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)   
 [ActiveX 控制項容器](../mfc/activex-control-containers.md)