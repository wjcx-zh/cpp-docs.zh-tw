---
title: "Creating a Tool Tip for a Toolbar Button | Microsoft Docs"
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
helpviewer_keywords: 
  - "tool tips [C++], adding to toolbar buttons"
  - "\n in tool tip"
  - "toolbar buttons [C++], tool tips"
  - "buttons [C++], tool tips"
  - "Toolbar editor, creating tool tips"
ms.assetid: 0af65342-fd78-4e78-8d0d-dc68f7fc462e
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Creating a Tool Tip for a Toolbar Button
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

### 若要建立工具提示  
  
1.  請選取工具列按鈕。  
  
2.  在[屬性視窗](../Topic/Properties%20Window.md)的 \[Prompt\] 屬性欄位中加入顯示在狀態列的按鈕說明；請在訊息之後加入 \\n 和工具提示名稱。  
  
 工具提示的常見範例為 WordPad 中的 \[列印\] 按鈕：  
  
 1.  開啟 WordPad。  
  
 2.  將滑鼠指標移到 \[列印\] 工具列按鈕上。  
  
 3.  請注意現在「列印」字樣已經在滑鼠指標下浮現。  
  
 4.  請查看 \[WordPad\] 視窗底部的狀態列，請注意它現在顯示出的是「列印使用中的文件」。  
  
 步驟 3 中的「列印」即為「工具提示名稱」，而步驟 4 內的「列印使用中的文件」則為「顯示在狀態列的按鈕說明」。  
  
 如果您希望使用**工具列**編輯器來建立此效果，請將 \[Prompt\] 屬性設為 \[列印使用中的文件\]。  
  
> [!NOTE]
>  您可使用[屬性視窗](../Topic/Properties%20Window.md)來編輯提示文字。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 需求  
  
 MFC 或 ATL  
  
## 請參閱  
 [Creating, Moving, and Editing Toolbar Buttons](../mfc/creating-moving-and-editing-toolbar-buttons.md)   
 [Toolbar Editor](../mfc/toolbar-editor.md)