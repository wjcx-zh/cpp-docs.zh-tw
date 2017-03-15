---
title: "Creating a New Toolbar Button | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.toolbar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Toolbar editor, creating buttons"
  - "toolbar buttons (in Toolbar editor), button image"
  - "toolbar buttons (in Toolbar editor), creating"
  - "toolbar buttons (in Toolbar editor)"
ms.assetid: 46c120fe-4f2a-4887-a08f-bd1fea04b3f4
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Creating a New Toolbar Button
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

### 若要建立新的工具列按鈕  
  
1.  在[資源檢視](../windows/resource-view-window.md)中展開資源資料夾 \(例如，Project1.rc\)。  
  
    > [!NOTE]
    >  如果您的專案並未包含 .rc 檔案，請參閱[建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  展開 \[工具列\] 資料夾，然後選取想要編輯的工具列。  
  
3.  為工具列右端的空白按鈕指定 ID。  您可在[屬性視窗](../Topic/Properties%20Window.md)中編輯 \[ID\] 屬性來進行指定。  例如，您可能想讓工具列按鈕的 ID 和功能表選項的一樣。  在此狀況下，請使用下拉式清單方塊來選取功能表選項的 **ID**。  
  
     \- 或 \-  
  
     選取工具列右端的空白按鈕 \(在 \[工具列檢視\] 窗格內\)，並開始繪圖。  程式將指派一預設的按鈕命令 ID \(ID\_BUTTON\<n\>\)。  
  
 您也可將影像複製並貼入工具列，以做為新的按鈕。  
  
#### 若要將影像加入工具列內做為按鈕  
  
1.  在[資源檢視](../windows/resource-view-window.md)中按兩下工具列來開啟它。  
  
2.  接下來，開啟想要加入工具列內的影像。  
  
    > [!NOTE]
    >  如果您使用 Visual Studio 開啟影像，則影像將以影像編輯器開啟。  您也可以其他的圖形程式開啟影像。  
  
3.  從 \[編輯\] 功能表中選擇 \[複製\]。  
  
4.  按一下來源視窗頂端的工具列索引標籤，以切換至該工具列。  
  
5.  在 \[編輯\] 功能表上選擇 \[貼上\]。  
  
     該影像將出現在工具列中做為新的按鈕。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
### 需求  
 MFC 或 ATL  
  
## 請參閱  
 [Toolbar Button Properties](../mfc/toolbar-button-properties.md)   
 [Creating, Moving, and Editing Toolbar Buttons](../mfc/creating-moving-and-editing-toolbar-buttons.md)   
 [Toolbar Editor](../mfc/toolbar-editor.md)